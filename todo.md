# Run-Pix project

<img src="images/logo.png" alt="Run-Pix" width="100"/> <span style="font-size: '2 rem';"> Run-PiX <small> AI based race management from your mobile</small></span>

# TODO : Design

## use case
* find timing from images
* for images for a bib

# problems


* Deploy Error: Could not load the default credentials. Browse to https://cloud.google.com/docs/authentication/getting-started for more information.
pnpm add @google-cloud/functions-framework

# Todo:

* check NaN:NaN:NanN for Race Timing from save_result()
* result publishing

arrayOfMins=_.chain(allEntries.value).filter(checkStatus).filter(checkBib).groupBy("bib").map((x,k)=>_.minBy(x,"timestamp")).value() 

keys_=_.words("bib name timestamp status waypoint gender ")
res=_.chain(allEntries.value).filter(checkBib).groupBy("bib").map((x,k)=>_.chain(x).minBy("timestamp").pick(keys_).value()).orderBy("timestamp").groupBy(x=>x.status+"-"+x.waypoint+'-'+x.gender).value()

* video capture
* user permissions
* timestamp update
* startlist screen
* photoStatus==available UI 
* timestamp from server
* Logic to add timing entry: need lot of work
* watch the queue traffic
* search for all images (in case of seach image has all face. current solution any faces)


### current 


* toast DONE
* Certification link from result (WIP) DONE
* router replace for event DONE

* lodash tree shaking (gone bad since _.chain does not work)
import {chain,cloneDeep,map,take,keys,orderBy,sumBy,pickBy,split,sortBy,tap,startsWith} as _ from 'lodash-es'  problematic

* rename API as /image as /api/facematch

* defect: merge two fields 'user' for start else 'userId'
* Event mgt UI finetuning
* backend changes
    * change image waypoint
* Start list
* SVG logos
    * event logos

### features

* **23sep**

* functions: reorg.
* sync problems in github and 2 laptops
* add pubsub trigger
* use debug

* **22Mar**

* Certification link from result (WIP)
* router replace for event
* lodash tree shaking (gone bad since _.chain does not work)
import {chain,cloneDeep,map,take,keys,orderBy,sumBy,pickBy,split,sortBy,tap,startsWith} as _ from 'lodash-es'

* rename API as /image as /api/facematch

* defect: merge two fields 'user' for start else 'userId'
* Event mgt UI finetuning
* backend changes
    * change image waypoint
* Start list
* SVG logos
    * event logos


* **14jan**
    * start list
    * finalize provisional timings
    * problems with results page /formatting
    * images everywhere

* **28sep**
    * face search
        * service that wakes up for performance
        * direct fetch (earlier option storage update->pubsub->eventarc->function)
        * find more images button (maxDist)
        * compress images before upload
        * progress bar
        * test scripts
        * racelist sorted
        * photoStatus to have: available, face, faceonly
        * JOB API: getdescriptors /api/eventscan
        * JOB API: cluster /api/eventcluster   
    * revamped race page race create me
        * cards vs data table
        * create new race button
        * races sorted desc
* **14May**
    * several WIP change for race management
    * function generated page has ext .png.jpg instead of .jpg
    * share url working now

* **24 Apr**
    * reading marked with text
    * race log / provisional changes
    * bib lookup 
    * timestamp from photo internal

* **18 Apr**
    * publish results
* **9 Apr**
    * race start stop
    * UI: edit race info
    * UI: Camera / zoom
* **1 Apr**
    * search by bib no or name
    * direct link to bib
    * dynamic page with OG tags
    * upload time bookmark
* **Mar 2023**
    * IMG: dynamic resize (backend)
    * Default watermark (blank)
    * two rows fixed/centerd
    * SC: FB share
    * Whatsapp share

### bugs
### roadmap
* highlight pictures for the race
* IMG: watermark
* SS: INSTA share
* separate upload bucket - low

* user profiles
* UI: Org/roles
* UI: Race results

* finisher certificate
* certificates https://www.npmjs.com/package/google-slides
* certificate pdf to PNG https://www.npmjs.com/package/pdf-to-png-converter

* online registration

* Shopping cart

* Azure porting face matching
###
* Functions
    * Upload
        * bucket selection

    * Image to JSON
        testing framework
        all text labels
    * Json to reading
        * match to regex pattern of bib (and partial matches too)
        * score confidence (height/picture_height)
            * img, date, text, score
        * entry  in the reading table
    * tiing selections

* Bulk upload
    * files by location


`<FileUpload name="demo[]" :customUpload="true" @uploader="myUploader" />`

* race coverage
 if all bibs are covered?