# IDA Data Seeder
## Overview
A Python utility to import data into IDA component.

## Dependent services
- All IDA Components (Internal Service, Auth Service, OTP Service)
- Data Share Service
- Kernel Key Manager Service (Data Share Service call Key Manager APIs to perform data encryption)
- PMS Service (To onboard partner for performing Authentication for the imported data)
- Websub Service (To publish the onboarded partner details to IDA Service) 


## Run

### Pre-requisites

- Initialize virtualenv:
    ```sh
    python3 -m venv ~/.venv/ida-seeder
    ```

- Install the python requirements:
    ```sh
    source ~/.venv/ida-seeder/bin/activate
    pip3 install -r requirements.txt
    deactivate
    ```
- Create a new folder `secrets-store` under data_seeder folder, The folder is used to store the secrets required for the seeder.
	-- Export `uin_hash_salt` table data from `ID_REPO` database from the environment and create an csv file with only id & slat values
	
	-- Example:
	```sh
    1,PwNa9oV+GtusHPxAumIssA== 
    ```
		
- Edit the environment related details in `config/config.toml` file. Refer comments in config file to update the necessary values.

- Data to be import should in a text file with an separator. Default separator is `|`. 
	-- Note:
	```sh
	The column header names in the text file should match with the master id schema field names. 
	```
	-- Mandatory column headers are `language`, `id or vid` 
		

### Run
```sh
python data_seeder/seeder_main.py
```
