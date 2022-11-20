# fleeting

fleeting is an extensible ephemeral cloud provider.

## Why?

fleeting exists because running development workloads that require cloud
infrastructure is too hard. Not only is managing permissions and access
difficult, but the consequences of making a mistake are potentially extremely
costly. This is unacceptable.

We believe you should be able to:
- Provision cloud infrastructure without worrying about cost.
- Provision cloud infrastructure without worrying about credentials.
- Share access to view cloud infrastructure without worrying about permissions.
- Prototype new kinds of cloud infrastructure and managed services.

Sound impossible? We don't think so.

## How does it work?

The secret of fleeting is that it actually isn't a cloud provider (in the
traditional sense) at all. All infrastructure runs on your machine. This is
accomplished by harnessing the power of your web browser, which turns out to be
a ubiqutous general purpose computing platform.

fleeting uses organizational units called "fleets" to group infrastructure and
access. The simplest way to conceptualize a fleet is as a browser tab. fleets
are initialized by going to [fleeting.cloud] and clicking "Create Fleet". At
this point, fleeting will redirect you to the console for your new fleet, which
is assigned a dedicated subdomain.

Behind the scenes, the following is happening:

- A [websocket] connection between your machine and [fleeting.cloud] is
  established. This is used to broadcast the state of infrastructure running on
  your machine to viewers on other machines.
- Credentials are generated and made available for copy in your browser window.
  These credentials are used to both provision and consume infrastructure.
- A console is displayed with available infrastructure services. Provisioning
  infrastructure, such as a SQL database, will cause an instance to be started
  in your browser.
- When a workload attampts to connect to the infrastructure (using the supplied
  credentials), a [WireGuard] tunnel is established between the machine running
  the fleet (i.e. the broswer), and the machine running the wokload.

## Frequently Asked Questions

**Who can view my infrastructure?**

All infrastructure is currently publicly viewable with a fleet link. fleeting is
not recommended for production use-cases and sensitive data should not be stored
in a fleet.

**How long does my infrastructure live?**

Because infrastructure runs in your browser, it lives as long as keep your fleet
tab open. Infrastructure will continue to run if network connection is lost.
fleeting will attempt to reconnect periodically.

## Project Status

This project is currently under development and not publicly available.

<!-- Named Links -->
[fleeting.cloud]: https://fleeting.cloud
[websocket]: https://www.rfc-editor.org/rfc/rfc6455
[WireGuard]: https://www.wireguard.com/
