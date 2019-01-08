# Agent Check: Neutrona

## Overview

This check monitors [Neutrona][1] cloud connectivity services to:
 - Azure (ExpressRoute)

## Setup

### Installation

The Neutrona check is not included in the [Datadog Agent][2] package, so you
need to install it.

You can copy the check files manually or run the _install.sh_ script if you are running the [Datadog Agent][2] on Debian/Ubuntu. This will copy both the check script and sample configuration file and **restart** the [Datadog Agent][2] :exclamation:. 


### Configuration

1. Edit the `neutrona.d/conf.yaml` file, in the `conf.d/` folder at the root of your
   Agent's configuration directory to start collecting your neutrona performance data.
   See the [sample neutrona.d/conf.yaml][2] for all available configuration options.

2. [Restart the Agent][3].

### Validation

[Run the Agent's status subcommand][4] and look for `neutrona` under the Checks section.

## Data Collected

### Azure Metrics

#### ExpressRoute Netowrk-to-Network Interface (NNI) Metrics

- **egress_bps:** Bits per second transmitted towards Azure over the ExpressRoute peering.

- **egress_interface_errors:** Presence or absence of egress errors in the ExpressRoute NNI (Network-to-Network Interface)

- **ingress_bps:** Bits per second received from Azure over the ExpressRoute peering.

- **ingress_interface_errors:** Presence or absence of ingress errors in the ExpressRoute NNI (Network-to-Network Interface)

- **output_optical_power:** Output optical power measured at the ExpressRoute NNI (Network-to-Network Interface)

- **receiver_optical_power:** Input optical power measured at the ExpressRoute NNI (Network-to-Network Interface)

- **tags:** Collection of tags

  - **"primary|secondary":** Peering over _primary_ or _secondary_ Express Route NNI.
  
  - **"ctag_xxx":**  Peering's inner VLAN tag (Customer VLAN tag)
  
#### ExpressRoute Performance Metrics - Customer Premises to ExpressRoute NNI
 - **Two_Way_Delay**: Round trip delay 
 - **Two_Way_DV**: Jitter (delay variation)
 - **Packet_Loss_Ratio**: Packet loss ratio
 - **tags:** Collection of tags
   - **performance:** Performance tag
   - **E2E|LLP:** _End-to-End_ or _Local Loop_ segments
                  
### Service Checks

Neutrona does not include any service checks at this time.

### Events

Neutrona does not include any events at this time.

## Troubleshooting

Need help? Contact [Datadog support][5].

[1]: https://telemetry.neutrona.com
[2]: https://github.com/DataDog/integrations-core/blob/master/neutrona/datadog_checks/neutrona/data/conf.yaml.example
[3]: https://docs.datadoghq.com/agent/faq/agent-commands/#start-stop-restart-the-agent
[4]: https://docs.datadoghq.com/agent/faq/agent-commands/#agent-status-and-information
[5]: https://docs.datadoghq.com/help/