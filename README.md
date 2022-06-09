# BackgroundPOC
 POC for completing Nretwork request in background using https://developer.apple.com/documentation/uikit/uiapplication/1623051-beginbackgroundtask
DispatchQueue.global().async {

            self.backgroundTaskID  = self.beginBackgroundUpdateTask()
             
            // Start first network request
            // After each request ( success , failure , error ) check if reach limit= 20 call end the backgroundTask else make the next call
            // each request contains lotID and images[] array of images files 
            self.sendAppDataToServer(lotNum: 1)
            
             
            }



scenarios: 
1- uploading about 8 requests in bg then stopped till reopen the app again , the interrupted request got connection error then upload the next one 

2- it didn't upload anything in bg

3- App terminated while it's in bg and reopen again when select it 

4- error in endbackground task once the app goes background although i didn't call it 
Can't end BackgroundTask: no background task exists with identifier 1 (0x1), or it may have already been ended. Break in UIApplicationEndBackgroundTaskError() to debug.
