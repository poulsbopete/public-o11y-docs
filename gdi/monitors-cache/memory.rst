.. _memory:

Memory usage
============

.. meta::
   :description: Use this Splunk Observability Cloud integration for the Memory monitor. See benefits, install, configuration, and metrics

.. note:: To collect memory utilization metrics only, use the native OTel component :ref:`host-metrics-receiver`.

The
:ref:`Splunk Distribution of OpenTelemetry Collector <otel-intro>`
uses the :ref:`Smart Agent receiver <smartagent-receiver>` with the
Memory monitor type to send memory usage stats for the underlying host.

On Linux hosts, this monitor type relies on the ``/proc`` file system.
If the underlying host's ``/proc`` file system is mounted somewhere
other than ``/proc``, set the path using the top-level configuration
``procPath``, as shown in the following example:

.. code-block:: yaml

   procPath: /proc

This integration is only available on Kubernetes and Linux.

Benefits
--------

.. include:: /_includes/benefits.rst

Installation
------------

.. include:: /_includes/collector-installation-linux.rst

Configuration
-------------

.. include:: /_includes/configuration.rst

Example
~~~~~~~

To activate this integration, add the following to your Collector
configuration:

.. code-block:: yaml

   monitors:
     smartagent/collectd/memory: 
       type: collectd/memory
       ... # Additional config

Next, add the monitor to the ``service.pipelines.metrics.receivers``
section of your configuration file:

.. code-block:: yaml

   service:
     pipelines:
       metrics:
         receivers: [smartagent/memory]

Metrics
-------

The following metrics are available for this integration:

.. raw:: html
 
      <div class="metrics-yaml" url="https://raw.githubusercontent.com/signalfx/splunk-otel-collector/main/internal/signalfx-agent/pkg/monitors/collectd/memory/metadata.yaml"></div>


Notes
~~~~~

.. include:: /_includes/metric-defs.rst

Troubleshooting
---------------

.. include:: /_includes/troubleshooting-components.rst
