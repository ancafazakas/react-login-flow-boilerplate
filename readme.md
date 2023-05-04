# Project breakdown
Step 1. Create/clone the git project

Step2. Login system flow and logic 

    2.1 System components and description
        1. register
            ->data collection: Mail, Firstname,Lastname, Date of birth, Password( Confirm Password)
            ->Account creation on the backend:
                * Phase 1. The data arrives from the client to the server (to the register endpoint). The backend creates the unverified account in the database and returns the 200 status message to the client
                    Mentions:
                        -The password won't be saved in plaintext, but rather a cryptographic hash will be run over the password 
                        
                * Phase 2. The client requests a verification email from the corresponding endpoint. An activation key will be generated and stored in the database for the respective client. The Backend will sends an email with the activation link (which will contain the activation key). The client accesses the link and sends the activation key back to the server  (to the corresponding endpoint) and the backend activates the account and sends the 200 status to the client.
        2. login
            -> the mail and the password will be collected and will be sent to the login endpoint.
            -> The cryptographic hash will be run over the password and the resulting hash will be compared with the stored password hash. If the comparison is valid, a jwt (json web token) will be generated 
        3.forgot password
            -> The account's mail will be sent to the coresponding route and the backend will send an email which contains another unique token for password reset in a URL that leads to the reset password page.
        4.reset password
            -> The user inputs the new password, which will be sent together with the token to the server.
            -> The server verifies the token and if it's valid, it will overwrite the old password.

Step 3. Technologies used
        Frontend: Reactjs (https://github.com/ancafazakas/react-login-flow-boilerplate)
        Backend: Nodejs (https://github.com/ancafazakas/nodejs-login-flow-boilerplate)  
        Db: MySql
