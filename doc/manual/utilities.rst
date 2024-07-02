Utilities
=========

.. Sort these tool by some subjective combination of their
   typical sequence and expected frequency of use.

ARTIQ Firmware Service (AFWS) client
------------------------------------

This tool serves as a client for building tailored firmware and gateware from M-Lab's servers and downloading the binaries in ready-to-flash format. It is necessary to have a valid subscription to AFWS. Subscription also includes general helpdesk support and can be purchased or extended by contacting ``sales@``. One year of support is included with most hardware purchased from M-Labs. 

.. argparse:: 
   :ref: artiq.frontend.afws_client.get_argparser
   :prog: afws_client 
   :nodescription: 
   :nodefault: 

   passwd 
      .. warning:: 
         After receiving your credentials from M-Labs, it is strongly recommended to change your password as soon as possible. Only alphanumeric symbols and underscores [a-zA-Z0-9\_] are allowed in AFWS passwords. If other symbols are input, they may be silently ignored, which can make logging in unpredictable or impossible. In emergencies passwords can be reset by contacting ``helpdesk@``.  
   
Static compiler
---------------

This tool compiles an experiment into a ELF file. It is primarily used to prepare binaries for the startup and idle kernels, loaded in non-volatile storage of the core device. Experiments compiled with this tool are not allowed to use RPCs, and their ``run`` entry point must be a kernel.

.. argparse::
   :ref: artiq.frontend.artiq_compile.get_argparser
   :prog: artiq_compile
   :nodescription:
   :nodefault: 

Flash storage image generator
-----------------------------

This tool compiles key/value pairs (e.g. configuration information) into a binary image suitable for flashing into the storage space of the core device. It can be used in combination with ``artiq_flash`` to configure the core device, but this is normally necessary at most to set the ``ip`` field; once the core device is reachable by network it is preferable to use ``artiq_coremgmt config``.  

.. argparse::
   :ref: artiq.frontend.artiq_mkfs.get_argparser
   :prog: artiq_mkfs
   :nodescription: 
   :nodefault: 

.. _flashing-loading-tool: 

Flashing/Loading tool
---------------------

.. argparse::
   :ref: artiq.frontend.artiq_flash.get_argparser
   :prog: artiq_flash
   :nodefault: 

.. _core-device-management-tool:

Core device management tool
---------------------------

The core management utility gives remote access to the core device logs, the :ref:`core-device-flash-storage`, and other management functions.

To use this tool, it is necessary to specify the IP address your core device can be contacted at. If no option is used, the utility will assume there is a file named ``device_db.py`` in the current directory containing the device database; otherwise, a device database file can be provided with ``--device-db`` or an address directly with ``--device`` (see also below).

.. argparse::
   :ref: artiq.frontend.artiq_coremgmt.get_argparser
   :prog: artiq_coremgmt
   :nodescription:
   :nodefault: 

Core device logging controller
------------------------------

.. argparse::
   :ref: artiq.frontend.aqctl_corelog.get_argparser
   :prog: aqctl_corelog
   :nodefault:

Device database template generator
----------------------------------

.. argparse:: 
   :ref: artiq.frontend.artiq_ddb_template.get_argparser
   :prog: artiq_ddb_template 
   :nodefault: 

ARTIQ RTIO monitor 
------------------

.. argparse::
   :ref: artiq.frontend.artiq_rtiomon.get_argparser 
   :prog: artiq_rtiomon  
   :nodefault: 

Moninj proxy
------------

.. argparse::
   :ref: artiq.frontend.aqctl_moninj_proxy.get_argparser
   :prog: aqctl_moninj_proxy
   :nodefault: 

.. _rtiomap-tool:

RTIO channel name map tool
--------------------------

.. argparse::
   :ref: artiq.frontend.artiq_rtiomap.get_argparser
   :prog: artiq_rtiomap
   :nodefault: 

.. _core-device-rtio-analyzer-tool:

Core device RTIO analyzer tool
------------------------------

This tool converts core device RTIO logs to VCD waveform files that are readable by third-party tools such as GtkWave. See :ref:`rtio-analyzer-example` for an example, or ``artiq.test.coredevice.test_analyzer`` for a relevant unit test. When using the ARTIQ dashboard, recorded data can be viewed or exported directly in the integrated waveform analyzer (the "Waveform" dock). 

.. argparse::
   :ref: artiq.frontend.artiq_coreanalyzer.get_argparser
   :prog: artiq_coreanalyzer
   :nodescription: 
   :nodefault: 

.. _routing-table-tool:

Core device RTIO analyzer proxy
-------------------------------

This tool distributes the core analyzer dump to several clients such as the dashboard. 

.. argparse::
   :ref: artiq.frontend.aqctl_coreanalyzer_proxy.get_argparser
   :prog: aqctl_coreanalyzer_proxy
   :nodescription:
   :nodefault: 

DRTIO routing table manipulation tool
-------------------------------------

.. argparse::
   :ref: artiq.frontend.artiq_route.get_argparser
   :prog: artiq_route
   :nodefault: 
