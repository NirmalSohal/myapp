# Graph DB Installation
Go to [GraphDB](https://www.ontotext.com/products/graphdb/graphdb-standard/) and request your GraphDB copy. You will receive an email with the download link. Proceed as follows:

### Installation on Linux

1. Download the GraphDB .rpm or .deb file.

2. Install the package with sudo rpm -i or sudo dpkg -i and the name of the downloaded package. Alternatively, you can double-click the package name.

3. Start the database by clicking the application icon. The GraphDB Server and Workbench open at http://localhost:7200/.

### Installation on Windows

1. Download your GraphDB distribution file and unzip it.

2. Start the GraphDB Server and Workbench interface by executing the graphdb startup script located in the $graphdb_home/bin folder:

3. A message appears in the console telling you that GraphDB has been started in Workbench mode. To access the Workbench, open http://localhost:7200/ in your browser.

### Installation using Docker 

* There are two editions of ontotext docker image available:
Standard: 9.8.0-se
Enterprize: 9.8.0-ee

`docker pull ontotext/<edition>`

* Starting a GraphDB instance:

`docker run -p 127.0.0.1:7200:7200 --name graphdb-instance-name -t ontotext/graphdb:tag`

where `graphdb-instance-name` : name you want to assign to your container ,`tag` : tag specifying the GraphDB version you want.

You can now go to http://localhost:7200 to see the database in action. Note that you will require a license to be able to use the database.

### Giving a license 

There are two ways to provide the license file

* provide the license in a virtual mounted home. On the host machine run

`mkdir -p data/conf
cp <path-to-license> data/conf/graphdb.license`

OR 

* extend the docker image and copy the license

`FROM ontotext/graphdb:tag
RUN mkdir -p /opt/graphdb/home/conf
COPY <path-to-license-on-host-machine> /opt/graphdb/home/conf` 

After providing license path, start the graphDB using 

`docker run -p 127.0.0.1:7200:7200 -v data:/opt/graphdb/home --name graphdb-instance-name -t ontotext/graphdb:tag`



