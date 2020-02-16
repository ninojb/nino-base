# nino-base
# Description
Schema repository. The aim of this repo is to list all object, fields, layouts for my dev environment and should replicate a package-based development model.

---
# Instructions on setting up the project

- **Create a Project in Visual Studio** 

sfdx force:project:create -n CMA 

- **Create  a folder named "nino-base" from the root directory of the CMA project**

- **Clone this repo in a folder under the project**

- **Update project definition file to include this repo** 

```
{
  "packageDirectories": [
    {
      "path": "force-app",
      "default": false
    },
    {
      "path": "nino-base",
      "default": true
    }
  ],
  "namespace": "",
  "sfdcLoginUrl": "https://login.salesforce.com",
  "sourceApiVersion": "46.0"
}
```

- **Update the Project Definition File to include feature required for this project**

```
{
  "orgName": "Demo Company",
  "edition": "Developer",
  "features": ["MultiCurrency"],
  "settings": {
    "lightningExperienceSettings": {
      "enableS1DesktopEnabled": true
    }
  }
}
```

- **Create a Scratch Org replacing ORG_NAME with the value you want and the DURATION in days(Ensure that you have authorized a devhub)**

```
sfdx force:org:create -f config/project-scratch-def.json -a <ORG_NAME>  -d <DURATION>
```

- **Set Default UserName (you can opt to set this when creating the scratch org above)**

```
sfdx force:config:set defaultusername=<ORG_NAME>
```

- **Add the below as part of .forceignore**

```
nino-base/README.md
```

- **Push the codes**

```
sfdx force:source:push
```

- **Assign the permission Set to the user**

```
sfdx force:user:permset:assign -n Car_Maintenance_App_Access
```