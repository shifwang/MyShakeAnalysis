## Overview of MyShake training data  

Data and demo is prepared by [Qingkai Kong](http://seismo.berkeley.edu/qingkaikong/) from [Berkeley Seismological Lab](http://seismo.berkeley.edu/). This data is part of training data for the [MyShake](http://myshake.berkeley.edu/) at Berkeley, please don't share this data to others outside of the class. Thanks. Have a great term project.  

---
### Folder structure
We have two folders:

* EQ
* Human

In the EQ folder, we have another two folders with earthquake data, one is from simulated data, and the other is from shake table tests. 

---
### Data format
Data is in JSON format. I just use '#' as comments.

```json
{
	{"header":
			{
				"stla": Number          #station latitude
				"stlo" Number           #station longitude
				"station": String       #station name
				"triggertime": Long     #station trigger time
				"starttime": Number     #record start time
				"sampling_rate": Number # sampling rate
				
				#Note, the following only exist in the simulated data
				"evla": Number          #earthquake latitude     
				"evlo": Number          #earthquake longitude
				"mag": Number           #earthquake magnitude
			}
	}
			
	{
	"data": 
			{
				"x": Array              #x component of acceleration (unit in g)
				"y": Array              #y component of acceleration (unit in g)
				"z": Array              #z component of acceleration (unit in g)  
			}
	}
	
}
```

I think you only need the data array of the 3 component acceleration, and the starttime and sampling_rate to get the timestamp. I put some other information just in case you need, but you can see a lot of the other information is missing. 

### Demo of reading data
Please check out the read\_data\_demo.ipynb in the folder for a quick start of reading data. 

### Note:
For the human data, we collected from MyShake app using a simple [STA/LTA](http://gfzpublic.gfz-potsdam.de/pubman/item/escidoc:4097:3/component/escidoc:4098/IS_8.1_rev1.pdf) algorithm, when the phone triggers, it record about 1 min data before the trigger and 4 min after. Therefore, the 'triggertime' field in the data is the time when the phone triggered (unix timestamp in sec), the data before that is from the before-trigger data. 

"triggertime": 1415004854.974, "starttime": 1415004764, the difference is always 90.? or 60.?, how to transform (unix timestamp in sec) to minutes? 
