# Fetching Documents 

## Fetching documents via the `fetcher.py` command line tool 

There is the `fetcher.py` tool with which you can fetch documents providing the start date, end date and output directory. It uses the `selenium` package and the Chromium Driver. The tool is located under `scripts/fetcher.py`. 

The script __requires__ the [Chrome Driver](http://chromedriver.chromium.org/downloads) in order to simulate a browser environment to fetch the needed documents from the [ET](http://et.gr). You can provide the `chromedriver` executable using the `--chromedriver` argument at the command line. 

Usage: 

```
$ fetcher.py -h
usage: fetcher.py [-h] -date_from DATE_FROM -date_to DATE_TO -output_dir
                  OUTPUT_DIR [--chromedriver CHROMEDRIVER] [--upload]

This is the fetching tool for downloading Government Gazette Issues from the
ET. For more information visit
https://github.com/eellak/gsoc2018-3gm/wiki/Fetching-Documents

optional arguments:
  -h, --help            show this help message and exit

required arguments:
  -date_from DATE_FROM  Date from in DD.MM.YYYY format
  -date_to DATE_TO      Date to in DD.MM.YYYY format
  -output_dir OUTPUT_DIR
                        Output Directory

optional arguments:
  --chromedriver CHROMEDRIVER
                        Chrome driver executable
  --upload              Upload to database
```
You need to provide the tool with the start and end date in DD.MM.YYYY format and the output directory of the documents. For example: 

```
fetcher.py -date_from 17.06.2018 -date_to 19.06.2018 -output_dir ./issues --chromedriver /usr/lib/chromium-browser/chromedriver
```

## Scheduling Document Fetching 

For a continuous integration scheme, it is advised to fetch documents from the [ET](http://et.gr) on a daily basis. This can be done using the `scripts/fetch_daily.sh` script that downloads documents on a daily basis. It can be used along with the `cron` tool in order for the task to be scheduled. A workaround for scheduling is shown below: 

1. To edit your `cron` configuration:

```bash
crontab -e
```

Add this command line:

```
30 2 * * * /path-to-project/scripts/fetch_daily.sh /output/dir
```

The crontab parses the following pattern: 
```
MIN HOUR DOM MON DOW CMD
```
The values allowed are the following: 

```
Format Meanings and Allowed Value:
MIN     Minute field    0 to 59
HOUR    Hour field      0 to 23
DOM     Day of Month    1-31
MON     Month field     1-12
DOW     Day Of Week     0-6
CMD     Command     Any command to be executed.
```

The daemon may need restart. For Debian-based systems:
```bash
sudo service crond restart
``` 

If you want to upload the newly fetched files to the database use the `--upload` flag.




