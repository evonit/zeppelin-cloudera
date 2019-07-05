# Apache Zeppelin parcel and CSD for Cloudera

This git repository is used to build both CSDs and parcels for CDH.

Zeppelin will run as service in Cloudera Manager, and its configuration is maintained through the CM web UI.
CSD has only python interpeter.

There are used Zeppelin 0.8.1.

This has been tested on CDH 5.15.2.

## Build

To build the CSDs and Parcels yourself, you can run the build script:

```
#Build the Parcel files, this make take some time
sh build.sh parcel

#Build the CSDs
sh build.sh csd
```

## Installation

Information about installing custom services can be found at [https://www.cloudera.com/documentation/enterprise/latest/topics/cm_mc_addon_services.html](https://www.cloudera.com/documentation/enterprise/latest/topics/cm_mc_addon_services.html).

```
# copy csd
cp ZEPPELIN-0.8.1.jar /opt/cloudera/csd/
chmod 644 ZEPPELIN-0.8.1.jar /opt/cloudera/csd/ZEPPELIN-0.8.1.jar
chown cloudera-scm:cloudera-scm ZEPPELIN-0.8.1.jar /opt/cloudera/csd/ZEPPELIN-0.8.1.jar
  
# copy parcel
cp ZEPPELIN-0.8.1_build/ZEPPELIN-0.8.1-el7.parcel /opt/cloudera/parcel-repo/
vi ZEPPELIN-0.8.1_build/ZEPPELIN-0.8.1-el7.parcel.sha
#copy hash string from ZEPPELIN-0.8.1_build/manifest.json
cp ZEPPELIN-0.8.1_build/ZEPPELIN-0.8.1-el7.parcel.sha /opt/cloudera/parcel-repo/
systemctl restart cloudera-scm-server
```
wait for restarting CM.
goto parcel menu, top-right on the CM web page, then you can find ZEPPELIN (if not, click Check for new parcels button, top-right on the screen)
click distribute button -> activate button
goto CM main -> add service -> find zeppelin
goto zeppelin -> start



## Configuration

TODO
