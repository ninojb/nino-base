# nino-base
# Description
Schema repository. The aim of this repo is to list all object, fields, layouts for my dev environment and should replicate a package-based development model.

Hi. I'm just wondering if I can book a hotel for my pet Kira 

January 25th to 27th


---


1) Create a Project in Visual Studio

sfdx force:project:create -n CMA 

2) Create  a folder named "nino-base" from the root directory of the CMA project

3) Clone this repo in a folder under the project

4) Update project definition file to include this repo 


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

5) Update the Project Definition File to include feature required for this project

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


6) Create a Scratch Org replacing ORG_NAME with the value you want and the DURATION in days(Ensure that you have authorized a devhub)
sfdx force:org:create -f config/project-scratch-def.json -a <ORG_NAME>  -d <DURATION>

7) Set Default UserName (you can opt to set this when creating the scratch org above)

sfdx force:config:set defaultusername=CMADev1

8) Add the below as part of .forceignore

nino-base/README.md

9) Push the codes 

sfdx force:source:push

10) Assign the permission set

sfdx force:user:permset:assign -n Car_Maintenance_App_Access