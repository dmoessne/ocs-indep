# ocs-indep

* this playbook is to run preperation steps from [official documented steps]( https://access.redhat.com/documentation/en-us/red_hat_openshift_container_storage/3.11/html/deployment_guide/chap-documentation-container_ready_storage_independent#CRS_Installing_Red_Hat_Storage_Server_on_Red_Hat_Enterprise_Linux_Layered_Install_independent)

* you have to ensure the following prereqs are applicable
  * needed repos are enabled, i.e.: rhel-7-server-rpms, rh-gluster-3-for-rhel-7-server-rpms
  * kernel version > `kernel-3.10.0-862.14.4.el7.x86_64` (RHEL 7.5 EUS or newer)

* it does the following:
   * installs required packages: redhat-storage-server, gluster-block
   * opens firewall for following tcp ports: 24010,3260,111,22,24007,24009,49152-49664 (only firewalld!)
   * enables permanently the following modules: dm_thin_pool, target_core_user, dm_multipath
   * ensures the following services are enabled: sshd, glusterd, gluster-blockd
   * checks for updates and if updates are found apply them and reboot the host
