Smart metering can utilize ZTA in several abstraction layers. From high-level, where the components may be thought of in a general networking context, to the hardware level, where a physical boundary historically stands as sufficient protection.

At a high-level glance (as seen in the model), the individual elements operate in a traditional network, where the Head End System (HES) receives connections and communicates to a multitude of entities. The point of this structure is that the HES has a connection to an Authentication service allowing all communication going to the HES to pass a PEP on each communicated message and established connection.
Any communication going from the HES is equally verifiable as data flowing in either direction upholds SPA, wherein commands and data are protected and signed only verifiable by the intended receiver.
Pictured is a connection to an Authentication service, handling identities and managing secrets, such that the HES is able to communicate securely with any identifiable entity.


![overview](https://user-images.githubusercontent.com/10893218/162294381-2a596144-c43c-4ae6-ae1c-22db65e37c01.png)


Communication between a meter and a collector tends to be required in RF networks  (or some Power Line Communication networks), where the collector operates as an infrastructure gateway between the HES and the meter.
The meter must not inherently trust the infrastructure but must be able to send and receive data from the HES. Applying ZTA, any packages sent are  protected, such that the HES - or the meter - is able to verify the sender and veracity of the information sent. This is continually done through an encrypted and signed SPA, verifying the sender, the traversed path, and the data.
The collector is used by the HES, to identify network paths and create SDN maps to establish knowledge of the currently identified and valid network entities. This information is essential in early warning against network attacks and in creating and updating Asset and Infrastructure Awareness.


![endpoint](https://user-images.githubusercontent.com/10893218/162297218-9ecde5f8-c997-4fd1-8a8f-1f75e4ffd4ab.png)

At the hardware level, the meter - as an example - could also operate with the ZTA approach. A central Processing and Policy component validates connections from other components, based on their roles and authorizations. Connections and information sent should be validated each time - depending on the nature of the component - and any information leaving the meter must be protected, such that an intended receiver may be able to understand and validate the meter's  identity.


![meter_specific](https://user-images.githubusercontent.com/10893218/162293498-3f4656ec-e0d8-4659-9564-34ffea31986c.png)
