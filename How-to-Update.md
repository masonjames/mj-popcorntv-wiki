## Updating using Git

If when you first downloaded and installed the project you just cloned the git repository, all you will need to do is run the following command, then you will be up to date! (you may also need to update your NPM packages if you have not updated in a while)
```
$ git pull
```

## If installed from a ZIP

If you originally installed the project by using a Zip file here are the steps that you need to take.  
1. Download the new version of PopcornTV  
2. Drag your config.json from the old version to the folder with the new version.  
3. Take the certificates from "assets/certificates/" and move them over to the new folder.  
4. Run ``sudo npm install`` again.  
5. Restart PopcornTV from the new folder.  