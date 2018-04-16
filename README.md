# SFDX MutualFundExplorer App
- These instructions demonstrate how to copy an Existing app from a package

## Setup
1. Create project
```
sfdx force:project:create -n sfdx-MutualFundExplorer
cd sfdx-MutualFundExplorer
```

2. Do GIT stuff (e.g. git init, create repo, add .gitignore)

3. Create a scratch org
```
sfdx force:org:create -f config/project-scratch-def.json -a TempUnmanaged
```

4. View config data for the scratch org
```
sfdx force:org:display -u TempUnmanaged
```

5. Create password
```
sfdx force:user:password:generate -u TempUnmanaged
```

6. View the config data again
```
sfdx force:org:display -u TempUnmanaged
```

7. Install the Unmanaged Package as instructed in:
```
https://trailhead.salesforce.com/trails/sfdx_get_started/modules/sfdx_app_dev/units/sfdx_app_dev_deploy
```

8. Create the Permission Set as instructed in: 
```
https://trailhead.salesforce.com/trails/sfdx_get_started/modules/sfdx_app_dev/units/sfdx_app_dev_deploy
```

9. Extract permission sets from scratch org
```
sfdx force:source:pull -u TempUnmanaged
```

10. Create a folder called `mdapipackage`
```
mkdir mdapipackage
```

11. Retrieve the contents of the DreamInvest package into the mdapipackage folder:
```
sfdx force:mdapi:retrieve -s -r ./mdapipackage -p DreamInvest -u TempUnmanaged -w 10
```

12. Change to the mdapipackage folder and verify that the unpackaged.zip file appears.
```
cd mdapipackage
```

13. Unzip `unpackaged.zip`
```
unzip unpackaged.zip -d .
```

14. Delete `unpackaged.zip`
```
rm unpackaged.zip
```

15. From the MutualFundExplorer folder, convert the contents of the mdapipackage folder
```
cd ..
sfdx force:mdapi:convert -r mdapipackage/
```

16. Delete `mdapipackage`
```
rm -rf mdapipackage
```

17. Delete scratch org
```
sfdx force:org:delete -u TempUnmanaged
```

---

## Dev, Build and Test

### Verify the App
1. Create new scratch org
```
sfdx force:org:create -s -f config/project-scratch-def.json
```

2. Push source and metadata to scratch org
```
sfdx force:source:push
```

3. Assign permission set
```
sfdx force:user:permset:assign -n DreamInvest 
```

### Deploy the Converted App Using Metadata API
- `Register Your Testing Environment` - Most of the time you’ll use a sandbox for testing, but for purposes of this module, go ahead and use your Trailhead Playground org for this step.

1. Log in to your Trailhead Playground org and create an alias for it.
```
sfdx force:auth:web:login -a MyTPO
```

2. Confirm that this org is available:
```
sfdx force:org:list
```

### Convert Source to Metadata API Format and Deploy
- Convert the source back to a format you can use with Metadata API.
1. Create mdapioutput
```
mkdir mdapioutput
```

2. Convert
```
sfdx force:source:convert -d mdapioutput/
```

3. Deploy
```
sfdx force:mdapi:deploy -d mdapioutput/ -u MyTPO -w 100
```

4. Assign permission set
```
sfdx force:user:permset:assign -n DreamInvest -u MyTPO
```

5. Run your tests and interact with the app:
```
sfdx force:org:open -u MyTPO
```


## Resources


## Description of Files and Directories


## Issues


