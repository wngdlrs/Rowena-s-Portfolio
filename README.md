# Rowena-s-Portfolio
*Analytics Portfolio*

## Project: Loading Data from HDFS to HBase

### Objective:
The objective of this project is to demonstrate the process of loading data from HDFS (Hadoop Distributed File System) into HBase, a NoSQL database that runs on top of Hadoop. The steps outlined below provide a clear and concise guide to achieving this task.

**HBase Architecture**

![Below is a detailed explanation of the key components and layers of the HBase architecture](/image/Hbase_Achitecture.jpg)

**Step-by-Step Guide:**

**1. Download Files using the wget command in the PuTTY Terminal.**
- *[movies.user](https://raw.githubusercontent.com/EbentheAnalyst/Hadoop/main/movies.user)*
- *[hbase.pig](https://raw.githubusercontent.com/EbentheAnalyst/Hadoop/main/hbase.pig)*

**2. Prepare HDFS:**
- Create a directory named 'pig' in HDFS using the following command:
   - *hadoop fs -mkdir /user/maria_dev/pig*
- Copy the 'movies.user' data file into the 'pig' directory in HDFS:
   - *hadoop fs -copyFromLocal movies.user /user/maria_dev/pig/movies.user*

**3. Initialize HBase Shell:**
- Log in to the HBase Shell:
   - *hbase shell*
- List the tables in HBase Shell to ensure no conflicts:
   - *list*
- Create an HBase table named 'users' with a column family 'userinfo':
   - *create 'users', 'userinfo'*
- List the tables again to confirm successful creation of the 'users' table
- Exit the HBase Shell:
   - *exit*  

**4. Execute Pig Script:**
- Check the contents of the 'hbase.pig' script to verify its correctness:
   - *less hbase.pig*
- Run the Pig script to execute the job of loading data into HBase:
   - *pig hbase.pig*
- Upon completion, the script will indicate successful storage of records in the 'users' HBase table.

**5. Verify Data Loading:**
- To confirm if the data has been successfully loaded, log back into the HBase Shell
- List the tables to ensure the 'users' table is present
- Once confirmed, display the records to check if the data loaded successfully:
   - *scan 'users'*

**6. Cleanup (Optional):**
- If needed, to clear everything and retry the process, it is important to first disbale the table and then drop the 'users' table
   - *disable 'users'*
   - *drop 'users'*

