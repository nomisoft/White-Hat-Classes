# CaptchaSecurityImages - PHP Catpcha

This script generates images (known as “Captcha’s”) which contain security codes used for protecting a form from spam bots. By encoding a 'password' inside an image and asking the user to re-enter what they see you can verify the user is a human and not automated software submitting your form. Why not try out the following form with valid and invalid codes to see how it works.

Update (27th March 2007): To stop spammers viewing the security code once and then continually submitting the form without requesting a new security image/code you should add the line unset($_SESSION['security_code']); when you are processing the form to clear the session

Update (7th February 2007): Due to a security bug in the script please ensure you are using the latest version

## Usage

You will also need to place a copy of the “Monofont” font in the same directory as the CaptchaSecurityImages.php file. (Alternatively you can replace the line var $font = ‘monofont.ttf’; with the name of whatever font you want to use)

Place the following code on your form. This will generate an image with a random string of characters along with the text field where the user will retype the code.

```
<img src="CaptchaSecurityImages.php" alt="" />
Security Code:
<input id="security_code" name="security_code" type="text" />
```

You can also specify certain options for the image by passing them as variables to CaptchaSecurityImages.php. The options available are the width and height of the image and the number of characters

```
<img src="CaptchaSecurityImages.php?width=100&amp;height=40&amp;characters=5" alt="captcha" />
<input id="security_code" name="security_code" type="text" />
```

Place the following in the code where the form is submitted to. This code will check what the user has typed matches the code in the image.

```
session_start();
if(($_SESSION['security_code'] == $_POST['security_code']) && (!empty($_SESSION['security_code'])) ) {
	// Insert you code for processing the form here, e.g emailing the submission, entering it into a database. 
	unset($_SESSION['security_code']);
} else {
	// Insert your code for showing an error message here
}
```

## Optional Extras

If you would rather your <img> tag links to a jpg rather than a php file you can use mod_rewrite. By inserting the following in your .htaccess file you can use <img src=”captcha.jpg” /> instead.

```
RewriteEngine on
RewriteRule captcha.jpg /CaptchaSecurityImages.php
```

You may wish to change the colour of the captcha image, this can be done by editing the background_colour, text_colour and noise_colour variables. The imagecolorallocate() function constucts a colour from the given RGB (red, green and blue) values, each of these is a number between 0-255. Another idea you might want to try is using the mt_rand function to randomize the colour each time a captcha is generated.
