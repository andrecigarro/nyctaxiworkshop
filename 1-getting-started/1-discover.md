# Discover the data

> [!TIP]
> All the services used in this workshop are available in both Ireland (eu-west-1) and N. Virginia (us-east-1), please use the one that best fits you.

## Prepare the environment and download the data

* Follow [this link](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page) and download the NYC Taxi and Limousine Commission data from any available month
 * In this workshop we will use the data from June/2020
 * You should end up with 4 files on your computer: 
   * **fhv_tripdata_YEAR-MONTH.csv**
   * **green_tripdata_YEAR-MONTH.csv**
   * **yellow_tripdata_YEAR-MONTH.csv**
   * **fhvhv_tripdata_YEAR-MONTH.csv**
* Open the [AWS Console](https://console.aws.amazon.com) and create an S3 Bucket to host your raw data
 * Use the following structure: 
   * username-serverless-analytics/
     * demo/ 
       * fhv/
       * green/
       * hvfhv/ 
       * yellow/
* Upload each one of the download .csv files to the corresponding S3 bucket
* Wait for all the uploads complete and move to the next section

