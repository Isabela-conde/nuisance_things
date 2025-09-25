
***Guide***

Create a openID account through IPSL node *- some nodes you can't access account settings*
https://esgf-node.ipsl.upmc.fr/projects/esgf-ipsl/

Go to 'Create Account' and follow instructions. Your login will be in. a http:// format

Login:
`https://esgf-node.ipsl.upmc.fr/esgf-idp/openid/username`
Password:
`pw`

go to any node to start searching for data needed.
https://esgf.llnl.gov/nodes.html

Once selected download weget script. Go through script and delete any years you don't need, most likely a better way to do this but ah well. 

Run sh file with 

`sh wget_script.sh`

### Some other things that were needed for me

Download wget
`brew install wget`

Download java
- all you need to do is search and go to web page, download mac version.

## The wget scripts downloaded from ESGF didn't end up working 

Using the names and urls form the downloaded wget file asked chatgpt to create a shell file that uses curl to download files. In terminal can use the following commands to create the shell file and run it. 
It'll be along the lines of: 
```
#!/bin/bash

# Set security level override for OpenSSL (if needed for ESGF servers)
export CURL_SSL_BACKEND=openssl
export OPENSSL_CONF=/opt/homebrew/etc/openssl@3/openssl.cnf  # Adjust if needed

# Embedded file list
read -r -d '' download_files <<EOF
'tos_Omon_GFDL-CM4_omip1_r1i1p1f1_gr_170801-172712.nc' 'https://esgf.ceda.ac.uk/thredds/fileServer/esg_cmip6/CMIP6/OMIP/NOAA-GFDL/GFDL-CM4/omip1/r1i1p1f1/Omon/tos/gr/v20180701/tos_Omon_GFDL-CM4_omip1_r1i1p1f1_gr_170801-172712.nc'
...
...
'tos_Omon_GFDL-CM4_omip1_r1i1p1f1_gr_198801-200712.nc' 'https://esgf.ceda.ac.uk/thredds/fileServer/esg_cmip6/CMIP6/OMIP/NOAA-GFDL/GFDL-CM4/omip1/r1i1p1f1/Omon/tos/gr/v20180701/tos_Omon_GFDL-CM4_omip1_r1i1p1f1_gr_198801-200712.nc'
EOF

# Loop through the embedded list
while read -r filename url; do
    filename=$(echo "$filename" | tr -d "'")
    echo "Downloading $filename..."
    curl -f --retry 5 --retry-delay 5 -o "$filename" "$url"

    if [[ $? -ne 0 ]]; then
        echo "Failed to download $filename"
    else
        echo "Downloaded $filename"
    fi
done <<< "$(echo "$download_files" | tr -s "'" ' ')"

```

go to folder that you want to save data: 

`cd /Users/isabelaconde/Desktop/omip/CESM2`

Create file 
```
touch download_cesm2_cm4.sh
nano download_cesm2_cm4.sh
```

Paste chatgpt text in to file 
save with ctrl+O, press enter, exit with ctrl+X

back in terminal, make file executable and run

```
chmod +x download_cesm2_cm4.sh
./download_cesm2_cm4.sh
````

```
#!/bin/bash

# Set security level override for OpenSSL (if needed for ESGF servers)
export CURL_SSL_BACKEND=openssl
export OPENSSL_CONF=/opt/homebrew/etc/openssl@3/openssl.cnf  # Adjust if needed

# Embedded file list
read -r -d '' download_files <<EOF
'thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_201501-204912.nc' 'https://esgf.ceda.ac.uk/thredds/fileServer/esg_cmip6/CMIP6/ScenarioMIP/MOHC/UKESM1-0-LL/ssp126/r4i1p1f2/Omon/thetao/gn/v20211202/thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_201501-204912.nc' 'SHA256' '2942ec0b25818bf42ed6ac17434b107655c0913ddcc0e126d98752987d25b79f'

'thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_205001-209912.nc' 'https://esgf.ceda.ac.uk/thredds/fileServer/esg_cmip6/CMIP6/ScenarioMIP/MOHC/UKESM1-0-LL/ssp126/r4i1p1f2/Omon/thetao/gn/v20211202/thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_205001-209912.nc' 'SHA256' '15a981e3ac88d02115ae56c98c619b722450c04e5513dd5c303c32086da6ad2a'

'thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_210001-210012.nc' 'https://esgf.ceda.ac.uk/thredds/fileServer/esg_cmip6/CMIP6/ScenarioMIP/MOHC/UKESM1-0-LL/ssp126/r4i1p1f2/Omon/thetao/gn/v20211202/thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_210001-210012.nc' 'SHA256' 'b8341c9b00bf0b47d81d20010b6f5664a33c459d8e361484cb2bc073bce2a5c6'

'thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_210101-214912.nc' 'https://esgf.ceda.ac.uk/thredds/fileServer/esg_cmip6/CMIP6/ScenarioMIP/MOHC/UKESM1-0-LL/ssp126/r4i1p1f2/Omon/thetao/gn/v20211202/thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_210101-214912.nc' 'SHA256' 'bf02568f3c31621957988b4be11090c83b2483f5c895dcf0251691c88a086f37'

'thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_215001-219912.nc' 'https://esgf.ceda.ac.uk/thredds/fileServer/esg_cmip6/CMIP6/ScenarioMIP/MOHC/UKESM1-0-LL/ssp126/r4i1p1f2/Omon/thetao/gn/v20211202/thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_215001-219912.nc' 'SHA256' '285fb611973248c4cd268bb3bb9b2cdea5f3b42c0bbfe73ff1d9a5231651700c'

'thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_220001-224912.nc' 'https://esgf.ceda.ac.uk/thredds/fileServer/esg_cmip6/CMIP6/ScenarioMIP/MOHC/UKESM1-0-LL/ssp126/r4i1p1f2/Omon/thetao/gn/v20211202/thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_220001-224912.nc' 'SHA256' '4773d3c97a73c60faa690bf4d1d6528987145810187580d7858be16799261668'

'thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_225001-229912.nc' 'https://esgf.ceda.ac.uk/thredds/fileServer/esg_cmip6/CMIP6/ScenarioMIP/MOHC/UKESM1-0-LL/ssp126/r4i1p1f2/Omon/thetao/gn/v20211202/thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_225001-229912.nc' 'SHA256' '383796c330217fdc1479bb3ae8986e2a7693bb2483adcf823b106c349c0ed31c'

'thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_230001-230012.nc' 'https://esgf.ceda.ac.uk/thredds/fileServer/esg_cmip6/CMIP6/ScenarioMIP/MOHC/UKESM1-0-LL/ssp126/r4i1p1f2/Omon/thetao/gn/v20211202/thetao_Omon_UKESM1-0-LL_ssp126_r4i1p1f2_gn_230001-230012.nc' 'SHA256' 'c6515e7151ae57a305635d6af2ff86e51b55362bb6e2639a6ac76b0dca56e3ea'
EOF

# Loop through the embedded list
while read -r filename url; do
    filename=$(echo "$filename" | tr -d "'")
    echo "Downloading $filename..."
    curl -f --retry 5 --retry-delay 5 -o "$filename" "$url"

    if [[ $? -ne 0 ]]; then
        echo "Failed to download $filename"
    else
        echo "Downloaded $filename"
    fi
done <<< "$(echo "$download_files" | tr -s "'" ' ')"
```