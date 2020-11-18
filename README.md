# Patient-Communication

https://cs673-patient-portal.herokuapp.com/home/index - go to https://cs673-patient-portal.herokuapp.com/users/sign_up if the above doesn't work

# Team Members:
 - Yaser Eisa **Team Manager**  
 - Lawrence Yang **Technical Lead** 
 - Richa Mehta
 - Paxton Edgar

Currently, all functioning source code is at https://github.com/YaserEisa/Project-. Will have to do some SCM cleanup [insert pivotal chore here]


# Product Vision:
For small medical practices, who need an easy to use and easy to manage patient communication and engagement, the PatientPortal is a cloud based medical practice management service that provides secure messaging, automates routine requests, and provides access to patient information and records. Unlike other services or software products, our product is easy to administer, simple to use, and available at moderate cost.

# Product Stake Holders:
 - Patients  
 - Doctors  
 - Doctor's assistants / Staff  

# User Personas:
 ![Alt text](https://github.com/YaserEisa/Patient-Communication/blob/master/User%20Personas/Cindy%20John%202.png?raw=true "User Persona")
 ![Alt text](https://github.com/YaserEisa/Patient-Communication/blob/master/User%20Personas/Mohamed%20Khan.png?raw=true "User Persona")
 ![Alt text](https://github.com/YaserEisa/Patient-Communication/blob/master/User%20Personas/Stacy%20Palma.png?raw=true "User Persona")

# Backlog Pivital Tracker URL:
https://www.pivotaltracker.com/n/projects/2466225


# Backlog Forecast Markdown:

|Id       |Title                                                                                             |Iteration Start|Iteration End|Type   |Estimate|Reasoning                                                                                           |
|---------|--------------------------------------------------------------------------------------------------|---------------|-------------|-------|--------|----------------------------------------------------------------------------------------------------|
|175004556|As a product developer, I want to setup a database for user accounts.                             |Sep 28, 2020   |Oct 4, 2020  |feature|5       |Schema design, multi team collaboration.                                                            |
|175004560|As a developer, I want to validate patient information with Patient Intake.                       |Sep 28, 2020   |Oct 4, 2020  |feature|3       |Need API to interface with from Patient intake for external call                                    |
|175002195|As a user interface designer, I want to sketch out a basic login page.                            |Sep 28, 2020   |Oct 4, 2020  |feature|2       |form design and internal DB call. Has to wait on DB launch                                          |
|175004596|As a medical office, I want to update patient information                                         |Oct 5, 2020    |Oct 11, 2020 |feature|3       |Multi team collaboration with multiple external call and validations through provided APIs          |
|175002198|As a patient, I want to create a user account (with patient validation).                          |Oct 5, 2020    |Oct 11, 2020 |feature|5       |Need API to interface with from Patient intake for external call                                    |
|175002229|As a medical practice, I want to create an account for a patient.                                 |Oct 12, 2020   |Oct 18, 2020 |feature|3       |Multi team collaboration with multiple external call and validations through provided APIs          |
|175002200|As a patient, I want to login with a username and password                                        |Oct 12, 2020   |Oct 18, 2020 |feature|2       |Form design and internal DB call. Has to wait on DB launch  Need API to interface for external call |
|175004590|As a product designer, I want to make a user account page.                                        |Oct 12, 2020   |Oct 18, 2020 |feature|2       |Form design and internal DB call. Has to wait on DB launch  Need API to interface for external call |
|175002201|As a patient, I want to view contact information.                                                 |Oct 12, 2020   |Oct 18, 2020 |feature|2       |Form design and internal DB call. Has to wait on DB launch  Need API to interface for external call |
|175004573|As a patient, I want to see my up coming visit(s) in Appointment Scheduling.                      |Oct 19, 2020   |Oct 25, 2020 |feature|5       |Form design and internal DB call. Has to wait on DB launch  Need API to interface for external call |
|175004534|As a patient, I want to update my email address.                                                  |Oct 19, 2020   |Oct 25, 2020 |feature|3       |Form design. Has to wait on DB launch  Need API to interface for external call                      |
|175004535|As a patient, I want to update my phone numbers.                                                  |Oct 19, 2020   |Oct 25, 2020 |feature|2       |Form design. Has to wait on DB launch  Need API to interface for external call                      |
|175004537|As a patient, I want to update my home address.                                                   |Oct 19, 2020   |Oct 25, 2020 |feature|2       |Form design. Has to wait on DB launch  Need API to interface for external call                      |
|175004544|As  patient, I want to receive a conformation email when my contact information has been updated. |Oct 26, 2020   |Nov 1, 2020  |feature|3       |Form design. Has to wait on DB launch  Need API to interface for external call                      |
|175002241|As a medical practice, I would like to broadcast messages to all patients.                        |Oct 26, 2020   |Nov 1, 2020  |feature|3       |Form design and internal DB call. Has to wait on DB launch  Need API to interface for external call |

# Process:
Team members came up with product vision and stories. Stories were placed into the Pivotal backlog. We then met in a planning meeting to go over the entire backlog, prioritize scenarios and stories (including an epic), and did a consensus estimate for story points. Focus was to get basic functionality - have patients login, view the most important information, and get some communication.

https://github.com/YaserEisa/Patient-Communication/blob/master/product_vision_rubric.md

# Database Schema: 

  **Users can be associated to multiple practices**
    Patients have a doctor for everything nowadays. Maybe I'm optimistic, but as we sell to multiple practices within a region, our database will 
    require some flexibility. This is done via the **MEMBERSHIPS** table. **MEMBERSHIPS** holds foreign keys to both **USERS** and **ACCOUNTS** so that
    we can associate any number of users to an account (say children who depend on their mother). To clarify, account alerts are tied to
    **MEMBERSHIPS**, but if an individual raises an issue, those issue relationships are tied to that individuals **USERS** record.
    **MEMBERSHIPS** also holds specific columns which allow for functions such as company messages, password reset, profile requests, etc. Additionally,
    **MEMBERSHIPS** possesses a column titled *Roles* - an user might be an administrator for a practice, the policy holder for an account, 
    or a dependent on an account - in the event that role specfic functions are added permission authentication can easily be performed. 
    **LOGINS** was segmented away from **USERS** for data integrity purposes. **LOGINS** accesses **USERS** via *ID* which holds a uniquness constraint. 
    Segmenting these reduced NULL managment and made reads significantly more efficient. 
    
![DB schema](https://user-images.githubusercontent.com/19698342/97622236-58f67f80-19fa-11eb-9eb1-77ad99ebac11.png)    
    
    
    
    
