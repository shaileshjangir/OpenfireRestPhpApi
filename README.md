OpenfireRestPhpApi
=====================

Use PHP to manage remote Openfire server using Rest Api of Openfire with restapi plugin.

## REQUIREMENTS
- PHP 5.4+

## INSTALLATION

### With Composer
-------------
You can install it via [composer](http://getcomposer.org/). Create `composer.json` file and add the requirement in require object, then run the `composer` install/update command.

```json
{
    "require": {
        "shaileshjangir/OpenfireRestPhpApi": "dev-master"
    }
}
```

## USAGE
```php
include "vendor/autoload.php";

// Create the Openfire Rest api object
$OfApi = new ShaileshJangir\OpenfireRestPhpApi\OpenfireRestPhpApi;

// Set the required config parameters
$OfApi->secret = "OpenFireRestSecret HERE";
$OfApi->host = "IP OR HOST NAME OF JABBER SERVER"; // default localhost
$OfApi->port = "9090";  // default 9090

// Optional parameters (showing default values)

$OfApi->useSSL = false;
$OfApi->plugin = "/plugins/restapi/v1";  // plugin 

// Add a new user to OpenFire and add to a group
$result = $OfApi->addUser('Username', 'Password', 'Real Name', 'johnsmith@example.com', array('Group 1'));

// Check result if command is succesful
if($result['status']) {
    // Display result, and check if it's an error or correct response
    echo 'Success: ';
    echo $result['message'];
} else {
    // Something went wrong, probably connection issues
    echo 'Error: ';
    echo $result['message'];
}

//Delete a user from OpenFire
$result = $OfApi->deleteUser($username);


//Disable a user
$result = $OfApi->lockoutUser($username);


//Enable a user
$result = $OfApi->unlockUser($username);

/**
 * Update a user
 *
 * The $password, $name, $email, $groups arguments are optional
 * 
 */
$result = $OfApi->updateUser($username, $password, $name, $email, $groups)

//Add to roster
$OfApi->addToRoster($username, $jid);

//Delete from roster
$OfApi->addToRoster($username, $jid);

//Update user roster
$OfApi->updateRoster($username, $jid, $nickname, $subscription]);

// Get all groups
$OfApi->getGroups();

// Retrieve group 
$OfApi->getGroup($name);

// Create a group
$OfApi->createGroup($group_name, $description);

// Update a group description
$OfApi->updateGroup($group_name, $description);

// Delete a group
$OfApi->deleteGroup($group_name);

```

## CONTACT
- Shailesh Jangir <shaileshjangir@gmail.com>
