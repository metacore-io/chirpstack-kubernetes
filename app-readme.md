# ChirpStack Application Server


ChirpStack Application Server is an open-source LoRaWAN Application Server, part of the
[ChirpStack](https://www.chirpstack.io/) open-source LoRaWAN Network Server stack. It is responsible
for the node "inventory" part of a LoRaWAN infrastructure, handling of received
application payloads and the downlink application payload queue. It comes
with a web-interface and API (RESTful JSON and gRPC) and supports authorization
by using JWT tokens (optional). Received payloads are published over MQTT
and payloads can be enqueued by using MQTT or the API.
