# Zevenet Loadbalancer

### Info:

By integrating with Zevenet, you add the ability to load balance services regardless of which hosts the containers have been deployed on. Currently, we only support an Zevenet Community Edition 5.0. Prior to adding the service, please make sure the farm is configured on the loadbalancer. 

After launching the HTTP service, services in Rancher will be registered to the Zevenet loadbalancer if it meets the following conditions:

* Exposes a public port on the host

* Contains a label with a key of 'io.rancher.service.external_lb_endpoint' and a value of the hostname pattern on Zevenet service

In the farm, the name of the service will be `<service_name>--U--<environment_uuid>--U--rancher`. You can configure the suffix of the names. By default, this is set as `rancher`.

Once the Zevenet configuration has been completed, you can access any services in Rancher using the Zevenet farm `<vip>:<port>` (if the url matches the host pattern). As services matching the criteria are added and removed from Rancher, these service will bet setup in the Zevenet farm.
