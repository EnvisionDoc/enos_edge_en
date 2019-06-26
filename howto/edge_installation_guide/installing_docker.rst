Installing Docker
===================

To install Docker, run the following commands

*Table: Step 1. Install docker*

.. list-table::
   :header-rows: 1

   * - Commands
     - Remarks
   * - yum install docker
     - Note: that is not docker-io but docker
   * - systemctl start docker
     - Start docker
   * - systemctl enable docker
     - Set docker as a startup item

*Table: Step 2. Create new mapping directory*

.. list-table::
   :header-rows: 1

   * - Commands
     - Remarks
   * - mkdir /root/dockerdata/box
     - /
   * - mkdir /root/dockerdata/data
     - /
   * - mkdir /root/dockerdata/config
     - /
   * - vim /etc/hosts
       10.21.3.16 registry.envisioncn.com
     - Add resolution
