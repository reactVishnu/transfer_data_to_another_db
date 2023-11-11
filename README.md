<p><a target="_blank" href="https://app.eraser.io/workspace/unlCADwgHzuK1NUv2vDg" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

# Seamless Data Migration: Effortless Transfer Between Databases 
Switch to another Deploying Env. without Losing Data .For e.g., switching from SQLite database to MySQL Database but you can use this way on any type of database.



## Transferring Data to another Db in a Django Application
Helps In Switch to another Deploying Env. without Losing Data

![image.png](/.eraser/unlCADwgHzuK1NUv2vDg___PyIGY6S3LKYuPtLSivFCFleXZbx2___csKiAD4H34q7g_rJKdhIq.png "image.png")

### Step 1: Generating a JSON file which includes your db content 
This command dumps the contents of your database in JSON format and saves it to a file named "**data.json**"

```
python manage.py dumpdata > data.json
```
![image.png](/.eraser/unlCADwgHzuK1NUv2vDg___PyIGY6S3LKYuPtLSivFCFleXZbx2___-a8V7M-YVGnagJXMS8Y-M.png "image.png")

**Note:** For excluding any models use "**_--exclude_**"

```
python manage.py dumpdata --exclude auth.permission --exclude contenttypes > data.json
```
### Step 2: Add your new database to the settings.
Add the new database to your **settings.py** file like this and run all your migrations for creating the table structure and DB schema.

![image.png](/.eraser/unlCADwgHzuK1NUv2vDg___PyIGY6S3LKYuPtLSivFCFleXZbx2___sKP2z0NARBCwF9BO7RDUo.png "image.png")

```
python manage.py migrate --database=new
```
**After migrations**

![image.png](/.eraser/unlCADwgHzuK1NUv2vDg___PyIGY6S3LKYuPtLSivFCFleXZbx2___SIjNokx9Jzq2oB6X0fs3C.png "image.png")

### Step 3: Convert the data.json to UTF-8 and Load your data into new db
Your data.json is of UTF-16LE and you need to convert it into UTF-8 and than load your data to new database.

![image.png](/.eraser/unlCADwgHzuK1NUv2vDg___PyIGY6S3LKYuPtLSivFCFleXZbx2___oY4EJget7utydKikFFWBH.png "image.png")

```
 python manage.py loaddata data.json --database=new
```


![image.png](/.eraser/unlCADwgHzuK1NUv2vDg___PyIGY6S3LKYuPtLSivFCFleXZbx2___jyMLzwTnlpu80y2g69J4v.png "image.png")

### Step 4: All data is succesfully transferred to new DB
 This process is useful for creating backups, migrating data between databases, or sharing sample data with others working on the project. Keep in mind that the `**dumpdata**` and `**loaddata**` commands are part of Django's serialization framework, and they work with various serialization formats, not just JSON.

![image.png](/.eraser/unlCADwgHzuK1NUv2vDg___PyIGY6S3LKYuPtLSivFCFleXZbx2___gJ9YIH6us0DifwnKzi1PZ.png "image.png")

## Contributing
If you would like to contribute to this project, please follow the guidelines in [CONTRIBUTING.md].

## License
This project is licensed under the 2023 Copyright - see the LICENSE.md file for details. 


<!--- Eraser file: https://app.eraser.io/workspace/unlCADwgHzuK1NUv2vDg --->