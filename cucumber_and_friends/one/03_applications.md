!SLIDE center transition=fade smaller

# Part 2: Security that matters

## Applications & Examples



!SLIDE code transition=fade smaller

    @@@ cucumber
    # Role management
    
    Scenario: Require login to edit profile
      Given I am not logged in
      When I visit the "Edit Profile" page for "Huey"
      Then I should see "You must login to access that page!"
          
    Scenario: User cannot edit another user's profile
      Given I am logged in as "Riley" with role: "Customer"
      When I visit the "Edit Profile" page for "Huey"
      Then I should see "You are not authorized!"

    Scenario: Customer cannot access admin functions
      Given I am logged in as "Riley" with role: "Customer"
      When I visit the "Admin" page
      Then I should see "You are not authorized!"



!SLIDE code transition=fade smaller

    @@@ cucumber
    # Secure pages
    
    Scenario: Require SSL for admin page
      Given I am logged in as "Grandpa" with role: "Admin"
      When I visit the "Admin" page
      Then the page should be secured with HTTPS
      
    Scenario: Redirect HTTP requests to HTTPS
      Given I am logged in as "Grandpa" with role: "Admin"
      When I visit the "Admin" page using an HTTP link
      Then I should be redirected to HTTPS      



!SLIDE code transition=fade evensmaller

    @@@ cucumber
    # Information leakage
    
    Scenario: Do not log credit card numbers
      Given I make a purchase using my credit card
      Then the log files should not contain my credit card number
      
    Scenario: Do not show user's contact info to strangers
      Given I am not logged in
      When I view the profile for "Uncle Ruckus"
      Then I should not see his email
      And I should not see his phone number



!SLIDE code transition=fade smaller

    @@@ cucumber
    # SSL setup
    
    Scenario: HTTPS web server
      Given a newly bootstrapped server
      When I install nginx 
      And I enable SSL on port 443
      Then the server should respond to HTTPS requests
      


!SLIDE code transition=fade evensmaller

    @@@ cucumber
    # Complex interactions
    
    Scenario: Request a new password
      Given a user "Huey" with email "huey@example.com"
      When he requests a new password
      Then he should receive an email with a password reset link
      
    Scenario: Reset password
      Given "Huey" has received an email with a password reset link      
      When he clicks the password reset link
      Then his password should be reset