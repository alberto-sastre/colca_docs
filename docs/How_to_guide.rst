How to guide
============


This guide tries to give you solutions for the topics you may face, to have
COLCA running suscessfully for you.


How to install COLCA
--------------------


For Colca installation just follow these steps:
:ref:`install_colca <installation_colca>`


How to install skforecast
-------------------------

For skforecast installation, just follow this step:
:ref:`install_skforecast <installation_skforecast>`



How to install and configure mongoDB
------------------------------------


For installating and configure MongoDB, just follow these steps:
:ref:`install_mongodb <initialization_mongodb>`



How to install and configure uvicorn
------------------------------------


For uvicorn installation and setup, just follow these steps:
:ref:`install_uvicorn <initialization_uvicorn>`


How to add 'processes' to the App
---------------------------------


For adding processes to the database:

.. code-block:: console

   (.venv) sascr/colca_services$ python3 -m add_processes


Now you have to complete the initial information for each process, one
at a time:

.. code-block:: console

   SETTING UP FIRST PROCESS: 
   Select city name: >> Madrid
   Select process name: >> Pump_Station_21
   Select need items: >> aluminium, oil

Or you can pass a list of objects to add to the system:

.. code-block:: console

   (.venv) sascr/colca_services$ python3 -m add_processes <list_of_processes>

Each element of *<list_of_processes>* must be a python dictionary with the
following key/value pattern:

.. code-block:: console

   city_name: str                                 
   co2_penalty: float                                
   id_number: int                                      
   last_updated: datetime ISO format          
   name: str                              
   needs_items: list of str                             
   new_needs: bool                                   
   new_orders: bool                                  
   purchase_orders_made: bool                        
   purchased_items: list of str        
   start_work: datetime ISO format           
   time_span: int                                   



How to remove 'processes' from the App
--------------------------------------

For removing processes to the database:

.. code-block:: console

   (.venv) sascr/colca_services$ python3 -m remove_processes <id_of_process>

Where <id_of_process> is the 'id-number' that you can find for each process info.

You can remove all processes from the database:

.. code-block:: console

   (.venv) sascr/colca_services$ python3 -m remove_processes -all

By specifying the ``all``  option, all processes in the database will be removed.

To avoid accidental remove of processes, you need to confirm this operation:

.. role:: red

.. parsed-literal::

   YOU ARE GOING TO REMOVE ALL INFORMATION IN DATABASE
   DO YOU WANT TO CONTINUE? PRESS 'Y' TO CONFIRM, ANY OTHER KEY TO CANCEL.

   :red:`WARNING!! THIS OPERATION CANNOT BE UNDONE!`



How to configure and run COLCA
------------------------------


For setting up and run COLCA App, follow the next steps in order:

1. First run the ``config`` file:

   .. code-block:: console

      (.venv) sascr/colca_services$ python3 config_colca

   You have to set the daily time for running COLCA App, press ``enter``:
   
   .. code-block:: console
      
      Select daily time execution for COLCA: >> 9:00
      


How to access the results
-------------------------


For viewing data from the database, you can use the ``data-view``:

   .. code-block:. console
      
      (.venv) sascr/colca_services$ python3 data-view

   You have to select an ``id_number`` of a process:

   .. code-block:: console

      Select a process 'id_number' to access information: >> 3

   You will be presented with the information on secreen as well as in XXX file:

   .. parsed-literal::

      EXTRACT OF PROCESS INFORMATION TAKEN FROM THE DATABASE (NOT AVAILABLE YET).



How to perform testing of the App
---------------------------------


To perform the suite test for the source the code, from the root run ``pytest``:

.. code-block:: console

   (.venv) sascr/pytest



How to update COLCA
-------------------

Updating COLCA...

