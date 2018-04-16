# SFDX MutualFundExplorer App

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





---

## Dev, Build and Test


## Resources


## Description of Files and Directories


## Issues


