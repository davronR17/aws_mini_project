# University Timetable Application

This project is the final submission for the COSC 2610 Operating Systems course.
It is a "University Timetable" web application developed using Flask and deployed on an AWS EC2 instance, with a PostgreSQL database hosted on AWS RDS.
The application enables users to select their academic level (Undergraduate or Graduate) and view a timetable of courses for that degree level.

Features
- Built with the Flask framework.
- PostgreSQL integration to manage course data.
- Deployed on AWS (EC2 for hosting, RDS for database).

Technologies Used
- Python (Flask framework)
- PostgreSQL
- AWS EC2 (for hosting)
- AWS RDS (for database)

Setup and Deployment Instructions

1. Set Up AWS Resources
- Create an AWS account and log in.
- Set up an EC2 instance along with the necessary security groups.
- Create a PostgreSQL database on AWS RDS, ensuring it has public access.

2. Connect to the EC2 Instance
Use this command to SSH into your EC2 instance:
ssh -i "C:\your_key_2_ec2.pem" ubuntu@<EC2_Public_IP>

3. Prepare the EC2 Instance
Update the instance and install the required dependencies:
sudo apt update
sudo apt install python3 python3-pip postgresql-client -y

4. Connect to the RDS PostgreSQL Database
Use the following command to connect to the database:
psql -h <RDS_End_Point> -U <RDS_User> -d <RDS_Database_Name>

5. Set Up the Database Table
Create the timetable table with the following SQL commands:
CREATE TABLE timetable (
    id SERIAL PRIMARY KEY,
    course_name VARCHAR(100),
    level VARCHAR(20),
    day VARCHAR(20),
    time VARCHAR(20)
);

INSERT INTO timetable (course_name, level, day, time)
VALUES
    ('Computer Languages', 'Undergraduate', 'Wednesday', '2:00 PM'),
    ('Operating Systems', 'Graduate', 'Tuesday', '2:00 PM'),
    ('Database Concepts', 'Graduate', 'Tuesday', '11:30 AM'),
    ('College Algebra', 'Undergraduate', 'Thursday', '9:00 AM'),
    ('Political Theory', 'Undergraduate', 'Monday', '4:20 PM');
    
6. Set Up the Flask Application
Create a project folder:
mkdir my_project
cd my_project
touch app.py

Implement the Flask application in app.py to connect to the PostgreSQL database.

7. Design HTML Templates
Create a templates folder and add index.html and timetable.html files with the required HTML code.

8. Set Up a Virtual Environment
Create and activate a Python virtual environment:
python3 -m venv venv
source venv/bin/activate

Also, need to install the following package:
pip3 install pg8000

9. Install Required Python Libraries
Install the necessary libraries:
pip3 install --upgrade pip
pip3 install flask psycopg2-binary

10. Run the Flask Application
Start the application with:
python app.py

11. Access the Application
Visit the application by opening a web browser and navigating to:
http://<EC2_Public_IP>:8000

Additional Notes
Make sure that your AWS security groups allow incoming HTTP traffic on port 8000.
Ensure the Flask app is correctly configured to connect to the RDS PostgreSQL database using the provided credentials.
