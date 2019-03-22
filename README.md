# Recaptcha V3 Java Example

Java example of Google reCAPTCHA v3 integration in a java web application 

  - server side: GoogleRecaptcha.java for recaptcha verification
  - client side: see below

# Client side part

  Add a hidden input field to your web form
  ```html
  <input type="hidden" id="captchatoken" name="captchatoken" size="1" value=""/>
  ```
  
  Include Google Recaptcha JavaScript libary
  ```html
  <script src="https://www.google.com/recaptcha/api.js?render=YOUR_PUBLIC_KEY"></script>
  ```
  
  Insert small JavaScript that fill hidden recaptcha token input field
  ```js
  <script>
	grecaptcha.ready(function() {
		grecaptcha.execute('YOUR_PUBLIC_KEY', {action: 'register'}).then(function(token) {
            $('#captchatoken').val(token)
		});
    });
 </script>
  ```
 # Server side verification
 After setting up the client side part, now you can verify the recaptcha token from client side on the server. If the user is valid (human) it will return true, if the user is a bot false
 ```java
 GoogleRecaptcha.isValid(captchatoken)
 ```



PS: I'm using this in a Play Framework 1 Web Application
