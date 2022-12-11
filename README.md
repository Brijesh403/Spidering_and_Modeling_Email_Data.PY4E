# Spidering_and_Modeling_Email_Data.PY4E
 * A project to download, process, and visualize an email corpus from the Sakai open source project from 2004-2011
 * Analyzing an EMAIL Archive from gmane and vizualizing the data
---
## Step 1 <sup>st</sup>
### Spidering the link and creating a database to store the mining.

*We will be spidering this link:* 
- (http://mbox.dr-chuck.net/)

By run of gmane.py getting the last five messages of the
sakai developer list:

```
How many messages:10
http://mbox.dr-chuck.net/sakai.devel/1/2 2662
    ggolden@umich.edu 2005-12-08T23:34:30-06:00 call for participation: developers documentation
http://mbox.dr-chuck.net/sakai.devel/2/3 2434
    csev@umich.edu 2005-12-09T00:58:01-05:00 report from the austin conference:  sakai developers break into song
http://mbox.dr-chuck.net/sakai.devel/3/4 3055
    kevin.carpenter@rsmart.com 2005-12-09T09:01:49-07:00 cas and sakai 1.5
http://mbox.dr-chuck.net/sakai.devel/4/5 11721
    michael.feldstein@suny.edu 2005-12-09T09:43:12-05:00 re: lms/vle rants/comments
http://mbox.dr-chuck.net/sakai.devel/5/6 9443
    john@caret.cam.ac.uk 2005-12-09T13:32:29+00:00 re: lms/vle rants/comments
Does not start with From 
```

*Note:The program scans content.sqlite from 1 up to the first message number not
already spidered and starts spidering at that message.  It continues spidering
until it has spidered the desired number of messages or it reaches a page
that does not appear to be a properly formatted message.*

## Step 2<sup>nd</sup>
### The second process is *running the program *gmodel.py.  

*gmodel.py* reads the rough/raw data from *content.sqlite* and produces a cleaned-up and well-modeled version of the data in the file index.sqlite The file  index.sqlite will be much smaller (often 10X smaller) than content.sqlite because it also compresses the header and body text.


*Running gmodel.py works as follows:*
```
Loaded allsenders 1588 and mapping 28 dns mapping 1
1 2005-12-08T23:34:30-06:00 ggolden22@mac.com
251 2005-12-22T10:03:20-08:00 tpamsler@ucdavis.edu
501 2006-01-12T11:17:34-05:00 lance@indiana.edu
751 2006-01-24T11:13:28-08:00 vrajgopalan@ucmerced.edu
```

## Step 3<sup>rd</sup>
### Running Gbasic.py

The first, simplest data analysis is to do a "who does the most" and "which 
organzation does the most"?  This is done using gbasic.py:

```
How many to dump? 5
Loaded messages= 51330 subjects= 25033 senders= 1584

Top 5 Email list participants
steve.swinsburg@gmail.com 2657
azeckoski@unicon.net 1742
ieb@tfd.co.uk 1591
csev@umich.edu 1304
david.horwitz@uct.ac.za 1184

Top 5 Email list organizations
gmail.com 7339
umich.edu 6243
uct.ac.za 2451
indiana.edu 2258
unicon.net 2055
```

## Step 4<sup>th</sup> : Visualizations

### First Vizualization by running gword.py.

![image](https://user-images.githubusercontent.com/100509604/206905349-c9b3dc8b-0185-4bab-ba27-86d23441f235.png)


There is a simple vizualization of the word frequence in the subject lines
in the file gword.py:

```
Range of counts: 33229 129
Output written to gword.js

This produces the file gword.js which you can visualize using the file 
*gword.htm.*
```
### Second visualization is in *gline.py.*

![image](https://user-images.githubusercontent.com/100509604/206905032-865dfab8-7ec2-4deb-8ece-ebc2c3d45dfc.png)


```
Loaded messages= 51330 subjects= 25033 senders= 1584
Top 10 Oranizations
>['gmail.com', 'umich.edu', 'uct.ac.za', 'indiana.edu', 'unicon.net', 'tfd.co.uk', 'berkeley.edu', 'longsight.com', 'stanford.edu', 'ox.ac.uk']
Output written to gline.js
```

##Its output is written to *gline.js* which is *visualized using gline.htm*.
