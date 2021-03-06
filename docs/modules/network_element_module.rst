.. _network_element:


network_element - Create, modify or delete network elements
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.5




.. contents::
   :local:
   :depth: 2


Synopsis
--------


* Each element type currently supported in this module is documented in the example playbook. Each network element type will have a minimum number of arguments that is required to create the element if it does not exist. Network elements supported by this module have their `create` constructors documented at http://smc-python.readthedocs.io/en/latest/pages/reference.html#elements. This module uses a 'update or create' logic, therefore it is not possible to create the same element twice. If the element exists and the attributes provided are different, the element will be updated before returned. It also means this module can be run multiple times with only slight modifications to the playbook. This is useful when an error is seen with a duplicate name, etc and you must re-adjust the playbook and re-run. For groups, you can reference a member by name which will require it to exist, or you can also specify the required options and create the element if it doesn't exist.



Requirements (on host that executes module)
-------------------------------------------

  * smc-python


Options
-------

.. raw:: html

    <table border=1 cellpadding=4>

    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
    <tr>
    <td rowspan="2">elements<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
    <td></td>
    <td>
        <div>A list of the elements to create, modify or remove</div>
    </tr>

    <tr>
    <td colspan="5">
        <table border=1 cellpadding=4>
        <caption><b>Dictionary object elements</b></caption>

        <tr>
        <th class="head">parameter</th>
        <th class="head">required</th>
        <th class="head">default</th>
        <th class="head">choices</th>
        <th class="head">comments</th>
        </tr>

        <tr>
        <td>netlink<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
        <td></td>
        <td>
            <div>Create a Static Netlink element</div>
        </td>
        </tr>

        <tr>
        <td>group<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
        <td></td>
        <td>
            <div>A group of network elements</div>
        </td>
        </tr>

        <tr>
        <td>network<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
        <td></td>
        <td>
            <div>A network element of type network</div>
        </td>
        </tr>

        <tr>
        <td>domain_name<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
        <td></td>
        <td>
            <div>Domain name element to be used in rule</div>
        </td>
        </tr>

        <tr>
        <td>host<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
        <td></td>
        <td>
            <div>A network element of type host</div>
        </td>
        </tr>

        <tr>
        <td>address_range<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
        <td></td>
        <td>
            <div>A network element of type address range</div>
        </td>
        </tr>

        <tr>
        <td>interface_zone<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
        <td></td>
        <td>
            <div>A zone tag optionally assigned to an interface</div>
        </td>
        </tr>

        <tr>
        <td>router<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
        <td></td>
        <td>
            <div>A router element</div>
        </td>
        </tr>

        <tr>
        <td>ip_list<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
        <td></td>
        <td>
            <div>An IP list element containing individual addresses and networks</div>
        </td>
        </tr>

        </table>

    </td>
    </tr>
    </td>
    </tr>

    <tr>
    <td>ignore_err_if_not_found<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
    <td></td>
	<td>
        <p>When deleting elements, whether to ignore an error if the element is not found. This is only used when <em>state=absent</em>.</p>
	</td>
	</tr>
    </td>
    </tr>

    <tr>
    <td>smc_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
    <td></td>
	<td>
        <p>FQDN with port of SMC. The default value is the environment variable <code>SMC_ADDRESS</code></p>
	</td>
	</tr>
    </td>
    </tr>

    <tr>
    <td>smc_alt_filepath<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
    <td></td>
	<td>
        <p>Provide an alternate path location to read the credentials from. File is expected to be stored in ~.smcrc. If provided, url and api_key settings are not required and will be ignored.</p>
	</td>
	</tr>
    </td>
    </tr>

    <tr>
    <td>smc_api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
    <td></td>
	<td>
        <p>API key for api client. The default value is the environment variable <code>SMC_API_KEY</code> Required if <em>url</em></p>
	</td>
	</tr>
    </td>
    </tr>

    <tr>
    <td>smc_api_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
    <td></td>
	<td>
        <p>Optional API version to connect to. If none is provided, the latest SMC version API will be used based on the Management Center version. Can be set though the environment variable <code>SMC_API_VERSION</code></p>
	</td>
	</tr>
    </td>
    </tr>

    <tr>
    <td>smc_domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
    <td></td>
	<td>
        <p>Optional domain to log in to. If no domain is provided, 'Shared Domain' is used. Can be set throuh the environment variable <code>SMC_DOMAIN</code></p>
	</td>
	</tr>
    </td>
    </tr>
    <tr>
    <td rowspan="2">smc_extra_args<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
    <td></td>
    <td>
        <div>Extra arguments to pass to login constructor. These are generally only used if specifically requested by support personnel.</div>
    </tr>

    <tr>
    <td colspan="5">
        <table border=1 cellpadding=4>
        <caption><b>Dictionary object smc_extra_args</b></caption>

        <tr>
        <th class="head">parameter</th>
        <th class="head">required</th>
        <th class="head">default</th>
        <th class="head">choices</th>
        <th class="head">comments</th>
        </tr>

        <tr>
        <td>verify<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>
            <div>Is the connection to SMC is HTTPS, you can set this to True, or provide a path to a client certificate to verify the SMC SSL certificate. You can also explicitly set this to False.</div>
        </td>
        </tr>

        </table>

    </td>
    </tr>
    </td>
    </tr>
    <tr>
    <td rowspan="2">smc_logging<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
    <td></td>
    <td>
        <div>Optionally enable SMC API logging to a file</div>
    </tr>

    <tr>
    <td colspan="5">
        <table border=1 cellpadding=4>
        <caption><b>Dictionary object smc_logging</b></caption>

        <tr>
        <th class="head">parameter</th>
        <th class="head">required</th>
        <th class="head">default</th>
        <th class="head">choices</th>
        <th class="head">comments</th>
        </tr>

        <tr>
        <td>path<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td></td>
        <td></td>
        <td>
            <div>Full path to the log file</div>
        </td>
        </tr>

        <tr>
        <td>level<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
        <td></td>
        <td>
            <div>Log level as specified by the standard python logging library, in int format. Default setting is logging.DEBUG.</div>
        </td>
        </tr>

        </table>

    </td>
    </tr>
    </td>
    </tr>

    <tr>
    <td>smc_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
    <td></td>
	<td>
        <p>Optional timeout for connections to the SMC. Can be set through environment <code>SMC_TIMEOUT</code></p>
	</td>
	</tr>
    </td>
    </tr>

    <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
    <td><ul><li>present</li><li>absent</li></ul></td>
	<td>
        <p>Create or delete flag</p>
	</td>
	</tr>
    </td>
    </tr>

    </table>
    </br>

Examples
--------

.. code-block:: yaml

    
    - name: Create a network element
      hosts: localhost
      gather_facts: no
      tasks:
      - name: Example network element creation
        register: result
        network_element:
          smc_logging:
            level: 10
            path: ansible-smc.log
          elements:
            - host: 
                name: hostb
                address: 1.1.1.1
                ipv6_address: 2001:0db8:85a3:0000:0000:8a2e:0370:7334
                secondary:
                  - 1.1.1.2
                  - 1.1.1.3
            - network:
                name: networka
                ipv4_network: 3.3.3.0/24
                ipv6_network: fc00::/7
                comment: created by dlepage
            - address_range:
                name: myrange
                ip_range: 1.1.1.1-1.1.1.10
            - interface_zone:
                name: myzone
            - domain_name:
                name: mydomain.com
                comment: foo
            - router:
                name: myrouter
                address: 172.18.1.254
                secondary:
                  - 172.18.1.253
                ipv6_address: 2003:dead:beef:4dad:23:46:bb:101
            - ip_list: 
                name: myiplist
                comment: testlist
                iplist:
                  - 1.1.1.1
                  - 1.1.1.2
                  - 1.1.1.3
                  - 1.1.1.4
            - group:
                name: foogroup
                #remove_members: true
                #append_lists: true
                members:
                    host:
                    - hosta
                    - hostb
                    network:
                    - networka
            - group:
                name: emptyregulargrp
                members:
            - router:
                name: myrouter2
                address: 13.13.13.13
            - network:
                name: mynetwork2
                ipv4_network: 13.13.13.0/24
            - netlink:
                name: mynetlink2
                gateway:
                    name: myrouter2
                    type: router
                network:
                -   mynetwork2
                domain_server_address:
                    -   8.8.8.8
                    -   8.8.7.7
                probe_address:
                    -   10.10.10.1
                comment: added by ansible
    
    
    - name: Delete network elements. Use a list of elements by name
      network_element:
        smc_logging:
            level: 10
            path: ansible-smc.log
        state: absent
        elements:
          - group:
              - mygroup
              - newgroupa
          - host:
              - hosta
              - hostb
          - network:
              - networka
          - address_range:
              - myrange
          - interface_zone:
              - myzone
          - domain_name:
              - mydomain.com
          - router:
              - myrouter
          - ip_list:
              - myiplist

Return Values
-------------

Common return values are documented `Return Values <http://docs.ansible.com/ansible/latest/common_return_values.html>`_, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>

    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

    <tr>
    <td>state</td>
    <td>
        <div>Current state of elements</div>
    </td>
    <td align=center>always</td>
    <td align=center>list</td>
    <td align=center>[{'action': 'created', 'type': 'tcp_service', 'name': 'myservice'}, {'type': 'tcp_service', 'name': 'newservice80'}, {'action': 'created', 'type': 'udp_service', 'name': 'myudp'}, {'type': 'udp_service', 'name': 'udp2000'}, {'action': 'created', 'type': 'ip_service', 'name': 'new service'}]</td>
    </tr>
    </table>
    </br></br>


Author
~~~~~~

    * David LePage (@gabstopper)




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


