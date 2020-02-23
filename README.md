# Windows Set-up

## Required files
1. PostgreSQL link is [here](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads)
2. **Python must be version 3.7 or there will be errors!** Link is [here](https://www.python.org/downloads/release/python-370/)

## Installation
1. Install PostgresSQL.
2. Open pgAdmin, and login using the password you setup. Head down to ```Login/Group Roles``` and right click and click create
3. Name your role admin and under ```Privileges``` make sure everything has been switched to yes.
4. Now right click ```Databases``` and click Create... > Database... Name your database mainframe and under ```Security``` click the + on ```Privileges```.
5. Select Grantee as admin and click Privileges and check off all and the top grant with options. Afterwards click Save and you are done setting up the database.
2. Install Python with PIP. **Make sure to check [x] Add Python 3.7 to Path**
3. run in powershell terminal
```
pip install virtualenv
```
4. At this point, in powershell type 
```
Get-ExecutionPolicy -list 
```
If it does not show
```
Scope              ExecutionPolicy
MachinePolicy      Undefined
UserPolicy         Undefined
Process            Undefined
CurrentUser        Undefined
LocalMachine       Unrestricted
```
then type
```
Set-ExecutionPolicy Unrestricted
```
to get the above screen. You can check by retyping Get-ExecutionPolicy-List.

5. Outside the repository run
```
virtualenv env
```
then run
```
. env\scripts\activate
```
6. Cd into the project and run
```
pip install requirements/default.txt
```
if that does not work go into the requirements folder and open default.txt. Install them one by one I.E.
```
pip install arrow panda etc. etc.
```
7. locate enviromental variables by going to control panel > systems & security > system > advanced system settings > click on enviromental variables. Under system variables click New... and in the dialog box under name copy and paste ```DJANGO_ENV_MODULE``` and under value copy and paste ```mainframe.settings.local```. Click OK to exit the dialog box and click ok 2 more times to save our settings.
8. Locate our projects folder through terminal, while having our env running, run
```
python manage.py migrate
```
to migrate our files to our server we created in step 5.

9. Once everything has finished migrating, run the server by typing in
```
python manage.py runserver
```
then navigate to
```
localhost:8000
```
to double check if the backend is up and running.

## Usage
To run the server start virtualenv
```
virtualenv env
```
then outside of the project run
```
. env\scripts\activate
```
after, go back into the project's main directory and run
```
python manage.py runserver
```

## Notes
If you have different versions of python installed remember to use
```
pip3 install example
```
to use python 3.0+

```And thank you Ryan for helping me with this! Could not have gotten it to work without his help.```