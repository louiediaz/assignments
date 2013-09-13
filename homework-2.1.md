# Homework 2.1 - Ever wonder what all these signs say?

For Homework 1.1, you found a nice project on Github, forked it into your own account, and cloned it into your Cloud 9 IDE account. For this assignment, pick one or more PHP files from your project (you DID pick a PHP project, didn't you?) and identify some of the following items of PHP grammar and vocabulary that we talked about in class, including but not limited to:

<<<<<<< HEAD
* Variables: `$name`
* Constants: `E_USER_WARNING`, `MY_AWESOME_CONSTANT`
* Arithmetic operators: addition (+), subtraction (-)
* Functions: `array_slice()`, `do_something_amazing()`

When you find one, identify the file and line number in this file, below the instrcutions per the example below. Try to make the indentation match the original file (yes, copy and paste), even if that means there's NO indentation. Crazy PHPers.

You don't have to identify EVERYTHING in a given line or even in a single file, but you may get extra points if you're thorough or make a survey of more than one file... And you might get docked if you make too much work for me. I at least want to see about 50 lines of code.

When you're done editing this file, save it, commit it, and push it to your "assignments" repo, called "origin". You remember how to push, right?

## Your work should look like this...

`path/to/file.php:3`
=======
* Variables: $name
* Constants: E_USER_WARNING, MY_AWESOME_CONSTANT
* Arithmetic operators: addition (+), subtraction (-)
* Functions: array_slice(), do_something_amazing()

When you find one, identify the file and line number in this file, below the instrcutions per the example below. Try to make the indentation match the original file (yes, copy and paste), even if that means there's NO indentation. Crazy PHPers.

You don't have to identify EVERYTHING in a given line or even in a single file, but you may get extra points if you're thorough or make a survey of more than one file... And you might get docked if you make too much work for me. ;)

When you're done editing this file, save it, commit it, and push it to your forked version of the "assignments" repo. Then open a pull request back to the original. YOU WILL NOT GET CREDIT IF YOU DO NOT OPEN A PULL REQUEST!

my_github_user/my_repository/path/to/file.php:3
>>>>>>> upstream/master
```php
    if ( MY_AWESOME_CONSTANT )
    // Constant: MY_AWESOME_CONSTANT
```

<<<<<<< HEAD
`path/to/file.php:42`
=======
my_github_user/my_repository/path/to/file.php:42
>>>>>>> upstream/master
```php
    $name = do_something_amazing() + 1;
    // Variable: $name
    // Function: do_something_amazing()
<<<<<<< HEAD
    // Literal: 1 (integer)
```

## Now get to it!


// Function: function db_init($dbconf)
{
    extract($dbconf);
    $dsn = $type === 'mysql'
        ? 'mysql:host=' . $host . ';port=' . $port . ';dbname=' . $name
        : 'sqlite:' . $path;
    try {
        $db = new PDO($dsn, $user, $pass);
        $db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        return $db;
    } catch (PDOException $e) {
        die('DB Connection failed: ' . $e->getMessage());
    }
}

// Function(s): db_init, extract, new PDO, setAttribute, catch, die, getMessage
// Variable(s): $dsn, $type, $host, $port, $name, $path, $dns, $user, $pass, $db, $e
// Literals(s): none

function create_user()
{
    $q = cfg('db')->prepare("
INSERT INTO users (user_name, user_password_hash, user_email)
VALUES(:user_name, :user_password_hash, :user_email)");

    $q->bindValue(":user_name", $_POST['user_name']);
    $q->bindValue(":user_password_hash", password_hash($_POST['user_password_new'], PASSWORD_DEFAULT));
    $q->bindValue(":user_email", $_POST['user_email']);
    if (!$q->execute()) throw new Exception(die($q->errorInfo()));
    $q->closeCursor();
}

// Function(s): create_user, cfg, prepare, bindValue, execute, closeCursor, if
// Variable(s): $q, $_POST, 
// Literals(s): none

function read_user($user)
{
    return cfg('db')->query("
SELECT user_name, user_email, user_password_hash
FROM users
WHERE user_name = '$user'")->fetch(PDO::FETCH_ASSOC);
}

// Function(s): read_user, return, SELECT, FROM, WHERE, fetch
// Variable(s): $user
// Literals(s): none

function update_user()
{
}

function delete_user()
{
}

function create_session($user)
{
    $_SESSION['user_name'] = $user['user_name'];
    $_SESSION['user_email'] = $user['user_email'];
    $_SESSION['user_logged_in'] = 1;
    $_SESSION['msg'] = $user['user_name'] . ' is now logged in';
}

// Function(s): create_session, msg
// Variable(s): $user, $_SESSION
// Literals(s): none
=======
```

al_the_x/some_awesome_project/path/to/some/file.php:42
```php
 if ( PHP == 'awesome' ) {
 // Constant: PHP
 // Comparison: ==
 // String: 'awesome'
```
>>>>>>> upstream/master
