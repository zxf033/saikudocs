Development
===========

Building Saiku
--------------

Get the source and create a local working branchClone the repository and setup a 'master' local branch.

.. code-block:: bash

    git clone git://github.com/OSBI/saiku.git

or if you are an authenticated committer, you would use..

.. code-block:: bash

    git clone git@github.com/OSBI/saiku.git

if developing off of a non-master branch, create local branch that tracks the remote branch

.. code-block:: bash

      git checkout -b somebranch origin/somebranch

Build all saiku projects (core libs + webapps for UI and backend)

.. code-block:: bash

    cd saiku && mvn clean install -DskipTests

The most commonly used package is the saiku-server package. It includes the saiku webapps deployed on a tomcat (with or without sample data). The server package with foodmart can be found at:

`./saiku/saiku-server/target/dist/saiku-server/`

cd there and run the script `start-saiku.sh` / `start-saiku.bat` depending on your platform. Saiku server will then be available (in Tomcat) at [http://localhost:8080](http://localhost:8080)

Warning It's important to have `JRE_HOME` set to the java install you want to use. Ubuntu and probably other linux distros by default install open-jdk (which will not run Saiku).

All other packages are available at :

`./saiku/saiku-server/target/`

Developing Saiku in Eclipse
---------------------------

Once you have cloned the public git repo (see step 1 above), you are left with a number of maven projects. These projects are setup for inclusion in Eclipse. If you want any Saiku going in any other IDE you need to use the according maven goal (like mvn eclipse)

Note In either case you may see warnings in Eclipse indicating a bad JRE reference in your build paths. If so, you need to adjust the JRE used in the Eclipse build path (for each project) to point it to a valid 1.6 JRE.

Import into Eclipse with Maven plugin
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you have an Eclipse plugin installed for Maven integration, such as [http://maven.apache.org/eclipse-plugin.html](http://maven.apache.org/eclipse-plugin.html), you can import Maven projects directly into Eclipse and the plugin will generate the correct Eclipse project metadata for you.

.. code-block:: text

    File->Import...
    Select Maven->Existing Maven Projects
    In "Root Directory" specify the root saiku folder
    Select which projects to import and then Finish

Let Maven generate Eclipse project files. Change directory into each of the three top level saiku projects and execute the 'eclipse' goal of the 'eclipse' Maven plugin like so:

.. code-block:: bash

    cd saiku-core && mvn eclipse:eclipse
    cd saiku-webapp && mvn eclipse:eclipse
    cd saiku-server && mvn eclipse:eclipse

Once you've done that, import the projects into your Eclipse workspace:

.. code-block:: bash

    File->Import...
    Select General->Existing Projects into Workspace
    Choose "Select Root Directory" and specify the root saiku folder
    Select which projects to import and then Finish

