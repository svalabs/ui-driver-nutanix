# ui-driver-nutanix
Rancher UI driver for the [nutanix docker-machine](https://github.com/nutanix/docker-machine) driver 

## Usage

* Add a Machine Driver in Rancher 2 (`Tools` -> `Drivers` -> `Node Drivers`)

| Key | Value |
| --- | ----- |
| Download URL | `TBD` |
| Custom UI URL | `TBD` |
| Whitelist Domains |  `TBD` |

* Wait for the driver to become "Active"
* Go to Clusters -> Add Cluster, your driver and custom UI should show up.

## Development

This package contains a small web-server that will serve up the custom driver UI at `http://localhost:3000/component.js`.  You can run this while developing and point the Rancher settings there.
* `npm start`
* The driver name can be optionally overridden: `npm start -- --name=DRIVERNAME`
* The compiled files are viewable at http://localhost:3000.
* **Note:** The development server does not currently automatically restart when files are changed.
* Do not use the `model.<drivername>Confg` signature to access your driver config in the template file, use the `config` alias that is already setup in the component

## Building

For other users to see your driver, you need to build it and host the output on a server accessible from their browsers.

* `npm run build`
* Copy the contents of the `dist` directory onto a webserver.
  * If your Rancher is configured to use HA or SSL, the server must also be available via HTTPS.

## Using

* Add a Machine Driver in Rancher 2.0 (Global -> Node Drivers)
  * Download URL: The URL for the driver binary (e.g. `https://github.com/nutanix/docker-machine/releases/download/v3.0.0-beta6/docker-machine-driver-nutanix_v3.0.0-beta6_linux`)
  * Custom UI URL: The URL you uploaded the `dist` folder to, e.g. `TBD`)
* Wait for the driver to become "Active"
* Go to Clusters -> Add Cluster, your driver and custom UI should show up.
