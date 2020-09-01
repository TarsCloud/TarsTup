[点我看中文版本](README.md)

## Description of agreement, tars file, and translation tool

**How `TARS encoding protocol`, `TUP grouping protocol`, and `TARS grouping protocol` correlate to one another:**

- The TARS encoding protocol is a data encoding and decoding rule, which encodes data types such as shaping, enumerated values, strings, sequences, dictionaries, and custom structures into a binary data stream according to certain rules. After the peer gets the binary data stream, it can be deserialized according to the corresponding rules to get the original value.

- The TARS encoding protocol uses an integer value (unsigned char) called TAG to identify variables. For example, the TAG value of a variable A is 100 (the value is defined by the developer). When we encode the variable value, we also encode the TAG value. When the peer needs to read the value of variable A, it searches for the data segment with the TAG value of 100 in the data stream and then reads the data part according to the rules that are the value of variable A.

- The positioning of the TARS coding protocol is a set of coding rules. The data serialized by the tars protocol can not only be transmitted over the network but can also be stored in the database.

- The TUP packet protocol is the upper layer encapsulation of the TARS encoding protocol and is positioned as a communication protocol. It uses the variable name as the keyword of the variable. When encoding, the client packs the variable name into the data stream; when decoding, the peer finds the corresponding data area according to the variable name and then deserializes the data area according to the data type to get the original value.

- The TUP package protocol has a built-in map type of TARS encoding protocol. The keyword of the map is the variable name, and the value of the map is the binary data serialized by TARS encoding the data value of the variable.

- The data packets encapsulated by the TUP packet protocol can be sent directly to the Tars server, and the server can directly deserialize to get the original value.

- TARS packet protocol is a communication protocol encapsulated by the TARS encoding protocol for RequestPacket (request structure) and ResponsePacket (result structure). The structure contains important information such as request serial number, protocol type, and binary data after serialization of RPC param

