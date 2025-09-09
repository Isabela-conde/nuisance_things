# Download MERRA2 data


1. Create earthdata account if you don't already have one, note down login and password
2. get .txt file from:
			https://disc.gsfc.nasa.gov/datasets?keywords=MERRA2&page=1&temporalResolution=1%20month
3. create a netcr file with earthdata login in and password
	- in terminal `nano ~/.netrc`
		- input the following: 
					```
					machine urs.earthdata.nasa.gov
					login your_username
					password your_password
				```
		- to exit cntrl + O , enter then cntrl + X
	- restrict file so only adim can read it `chmod 600 ~/.netrc`
	- then use `curl` in bash to get files 
		- `cat ~/Desktop/urls.txt | tr -d '\r' | xargs -n 1 curl -LJO -n -c ~/.urs_cookies -b ~/.urs_cookies`
		- where `~/Desktop/urls.txt` is the file path to the downloaded urls 
