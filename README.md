CloudStack PHP Client
=====================

PHP client library for the CloudStack Domain API v4.2 (Reference : http://cloudstack.apache.org/docs/api/apidocs-4.2/TOC_Domain_Admin.html)

Generate with the CloudStack client generator [demarey/cloudstack-client-generator](https://github.com/demarey/cloudstack-client-generator),
others languages are available. Check out this project to know more about it.

Examples
--------

Initialization

    $cloudstack = new CloudStackClient(API_ENDPOINT, API_KEY, SECRET_KEY);
   
Lists

    $vms = $cloudstack->listVirtualMachines();
    foreach ($vms as $vm) {
        echo("{$vm->id} : {$vm->name} {$vm->state}<br>");
    }
   
Asynchronous tasks

    $job = $cloudstack->deployVirtualMachine(1, 259, 1);
    echo("VM being deployed. Job id = {$job->jobid}<br>");
    
    echo("All jobs :<br>");
    foreach ($cloudstack->listAsyncJobs() as $job) {
        echo("{$job->jobid} : {$job->cmd}, status = {$job->jobstatus}<br>");
    }
