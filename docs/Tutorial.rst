Tutorial
========

This tutorial guides you in running a simulation with COLCA App, step by step.


.. _installation_colca:


Installation of COLCA App
-------------------------

To use COLCA, first clone COLCA from the GitHub repo:

.. code-block:: console

   (.venv) $ git clone https://github.com/alberto-sastre/Project2_AS.git



.. _installation_skforecast:


Installation of skforecast
--------------------------

You have to install ``skforecast`` package from the github repository

.. code-block:: console

   (.venv) $ pip install git+https://github.com/JoaquinAmatRodrigo/skforecast@v0.1.9




.. _initialization_mongodb:


Initialization of mongoDB
-------------------------

You have to install mongoDB and should have it running on your system.

If you have installed the MongoDB 4.4 Community Edition, you have to run MongoDB as a background service in terminal:

.. code-block:: console

  (.venv) $ brew services start mongodb-community@4.4

If you are working under Windows OS,  by installing MongoDB in Windows you can install it 
as a background service (mongoDB installer will ask you for this option) and it will be available 
at running time.


.. _initialization_uvicorn:


Initialization of uvicorn
-------------------------

First, install uvicorn in your virtual enviroment using pip:

.. code-block:: console

   (.venv) $ pip install uvicorn


Second, execute uvicorn in terminal:


.. code-block:: console

   (.venv) sascr/colca_services$ uvicorn colca:app --reload


Third, do not close this terminal until the end of the simulation.



Run the simulation
------------------

Now you are ready to run the simulation, to do this:

.. code-block:: console

   (.venv) sascr/colca_tutorial$ python3 -m tutorial


It takes a while to complete, not much ;)


First, you have to setup 2 processes in order to perform a simulation.
For this, you have to follow the instructions on screen, step by step.
We recommend you to use the 'default' values, it is easier.

1. You have to define a city name for a process:

   .. code-block:: console
      
      SETTING UP FIRST PROCESS: 
      Select city name: [Oviedo, Aviles]; default: Oviedo >>

#. You have to give a name to the process (to get it correctly idetified):

   .. code-block:: console

      Select process name: [Pump Station 1, Pump Station 2]; default: Pump Station 1 >>

#. You have to select what does your process need (for instance, oil):

   .. code-block:: console

      Select need items: [oil, rhodium, aluminium]; default: oil >>

#. You have to do the same with the second process:

   .. code-block:: console

      SETTING UP SECOND PROCESS: 
      Select city name: [Oviedo, Aviles]; default: Aviles >>

Second, once you have your processes defined, you will see the description
of then on screen. Now, you can press any button to start the simulation:

.. code-block:: console

   THESE ARE THE TWO PROCESSES WITH FULL DATA:


   city_name: Oviedo                                 city_name: Aviles
   co2_penalty: 23.44                                co2_penalty: 23.44
   id_number: 1                                      id_number: 2
   last_updated: 2021-06-04T06:20:37.185000          last_updated: 2021-06-04T06:20:37.185000
   name: Pump Station 1                              name: Pump Station 2
   needs_items: ['oil']                              needs_items: ['aluminium']
   new_needs: True                                   new_needs: True
   new_orders: True                                  new_orders: True
   purchase_orders_made: True                        purchase_orders_made: True
   purchased_items: ['gasoline', 'aluminium']        purchased_items: ['gasoline', 'aluminium']
   start_work: 2021-06-04T06:20:37.184000            start_work: 2021-06-04T06:20:37.184000
   time_span: 1200                                   time_span: 1200



Finally you will be presented with the **simulation results** on screen. You can
also access to this data in a ``.log`` file where all the same information is available:

.. role:: green

.. parsed-literal::
     
   RESULTS OF THE SIMULATION, IN :green:`GREEN` COLOR YOU CAN SEE THE CHANGES:


   city_name: Oviedo                                 city_name: Oviedo
   co2_penalty: 0                                    co2_penalty: :green:`23.44`
   id_number: 1                                      id_number: 1
   last_updated: 2021-06-04T06:20:37.185000          last_updated: :green:`2021-06-14T07:37:42.321000`
   name: pump station 21                             name: pump station 21
   needs_items: ['oil', 'rhodium']                   needs_items: ['oil', 'rhodium']
   new_needs: True                                   new_needs: True
   new_orders: True                                  new_orders: :green:`True`
   purchase_orders_made: True                        purchase_orders_made: :green:`True`
   purchased_items: ['gasoline', 'aluminium']        purchased_items: :green:`['oil', 'rhodium']`
   start_work: 2021-06-04T06:20:37.184000            start_work: :green:`2021-06-14T15:00:00.000000`
   time_span: 1200                                   time_span: :green:`2465`



Interpreting the results
------------------------

Once you have the results of the simulation, either in the ``.log`` file or in screen,
we can make an interpretation of the results with you, in order to extract useful information.

1. co2_penalty

   .. parsed-literal::

      co2_penalty: 0          co2_penalty: :green:`23.44`

   Indicates de c02_penalty, expressed in the currency of the country. 
   It applies when the process has to get power from a non-renewal source.


#. last_updated

   .. parsed-literal::

      last_updated: 2021-06-04T06:20:37.185000          last_updated: :green:`2021-06-14T07:37:42.321000`

   When this process was updated for the last time.


#. new_orders

   .. parsed-literal::

      new_orders: True        new_orders: :green:`True`

   If COLCA determines that there are new orders, it uses this flag, setting it to ``True``.


#. purchase_orders_made

   .. parsed-literal::

      purchase_orders_made: True        purchase_orders_made: :green:`True`

   If COLCA made a purchase of any element needed by the process, this flag is set to ``True``.


#. purchased_items

   .. parsed-literal::

      purchased_items: ['gasoline', 'aluminium']        purchased_items: :green:`['oil', 'rhodium']`

   This is a list of elements that COLCA has purchasd automatically for the process in order
   to cover the process's needs.


#. start_work

   .. parsed-literal::

      start_work: 2021-06-04T06:20:37.184000            start_work: :green:`2021-06-14T15:00:00.000000`

   This is the optimal date and time when the process has to start working.   


#. time-span

   .. parsed-literal::

      time_span: 1200         time_span: :green:`2465`

   This is the time window for optimizing the energy used by the process, in order to avoid
   co2 emissions and get the better energy price (if needed a non-renewable source).  


End of the simulation
---------------------
   
COLCA's simulation has come to its end. With this simulation you have seen how COLCA works
very fast, analyzing the processes and making the best decisions for them. Keeps the 
information of each process updated, and an accountability oc co2 emissions and side costs
could be easily performed.

In production, this is a fully automated process. Just add a process with the setup information
and let COLCA help you going Green!




.. note::
   
   You can also pip install ``requirements.txt`` to get all dependencies
   in your environment at once. You have to do this from the same folder
   where ``requierements.txt`` is stored:

   .. code-block:: console

      (.venv) $ pip install -r requirements.txt



