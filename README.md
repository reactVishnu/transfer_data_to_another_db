# Seamless Data Migration: Effortless Transfer Between Databases 
Switch to another Deploying Env. without Losing Data .For e.g., switching from SQLite database to MySQL Database but you can use this way on any type of database.



## Transferring Data to another Db in a Django Application
Helps In Switch to another Deploying Env. without Losing Data

![image.png](https://eraser.imgix.net/workspaces/unlCADwgHzuK1NUv2vDg/PyIGY6S3LKYuPtLSivFCFleXZbx2/csKiAD4H34q7g_rJKdhIq.png?ixlib=js-3.7.0 "image.png")

### Step 1: Generating a JSON file which includes your db content 
This command dumps the contents of your database in JSON format and saves it to a file named "**data.json**"

```
python manage.py dumpdata > data.json
```
![image.png](https://eraser.imgix.net/workspaces/unlCADwgHzuK1NUv2vDg/PyIGY6S3LKYuPtLSivFCFleXZbx2/-a8V7M-YVGnagJXMS8Y-M.png?ixlib=js-3.7.0 "image.png")

**Note:** For excluding any models use "**_--exclude_**"

```
python manage.py dumpdata --exclude auth.permission --exclude contenttypes > data.json
```
### Step 2: Add your new database to the settings.
Add the new database to your **settings.py** file like this and run all your migrations for creating the table structure and DB schema.

![image.png](https://eraser.imgix.net/workspaces/unlCADwgHzuK1NUv2vDg/PyIGY6S3LKYuPtLSivFCFleXZbx2/sKP2z0NARBCwF9BO7RDUo.png?ixlib=js-3.7.0 "image.png")

```
python manage.py migrate --database=new
```
**After migrations**

![image.png](https://eraser.imgix.net/workspaces/unlCADwgHzuK1NUv2vDg/PyIGY6S3LKYuPtLSivFCFleXZbx2/SIjNokx9Jzq2oB6X0fs3C.png?ixlib=js-3.7.0 "image.png")

### Step 3: Convert the data.json to UTF-8 and Load your data into new db
Your data.json is of UTF-16LE and you need to convert it into UTF-8 and than load your data to new database.

![image.png](https://eraser.imgix.net/workspaces/unlCADwgHzuK1NUv2vDg/PyIGY6S3LKYuPtLSivFCFleXZbx2/oY4EJget7utydKikFFWBH.png?ixlib=js-3.7.0 "image.png")

```
 python manage.py loaddata data.json --database=new
```


![image.png](https://eraser.imgix.net/workspaces/unlCADwgHzuK1NUv2vDg/PyIGY6S3LKYuPtLSivFCFleXZbx2/jyMLzwTnlpu80y2g69J4v.png?ixlib=js-3.7.0 "image.png")

### Step 4: All data is succesfully transferred to new DB
 This process is useful for creating backups, migrating data between databases, or sharing sample data with others working on the project. Keep in mind that the `**dumpdata**` and `**loaddata**` commands are part of Django's serialization framework, and they work with various serialization formats, not just JSON.

![image.png](https://eraser.imgix.net/workspaces/unlCADwgHzuK1NUv2vDg/PyIGY6S3LKYuPtLSivFCFleXZbx2/Mp33VpW-BnfkKLFdVx1jt.png?ixlib=js-3.7.0 "image.png")



