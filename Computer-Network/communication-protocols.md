# Communication protocol

## Overview 
- A communication protocol is a system of rules allowing two or more entities of a communication system to transmit information via varations of physical quanitites. The protocol defines the rules, syntax, semantics, and synchronization of communication and possible error recovery methods. Protocols can be implemented by hardware, software, or a combination fo the two. 
- Communication systems use well-defined formats for exchanging vairous messages. Each message has an exact meaning inteded to elicit a specific response from a range of posible responses predetermined for that particular situation. The specified behavior is typically independnet of how it is implemented. Communication protocols have to be agrred upon by the parties involved to reach a standardized implimentation of the protocol. To reach an agreement, a procol can be developed into a technical standard. A programming language describes the same for computers so there is an analogy between the two. 
- Multiple protocols often describe different aspects of a single communication. A group of protocols designed to work together is known as a protocol suite, and then they are implimented into a software they are a protocol stack. 
- Internet communication protocols are published by the Internet Engineering Task Force (IETF). THe Institute of Electitrical and Electronics engineers (IEEE) handles the wires and wireless networking and the International Organization for Standarization (ISO) Handles other types of networks. 
  
## Types of communication Protocols
- There are two primary types of communication protocols, based on their representation fo the content being carried.
### Text based
- A text based protocol, or plain text protocol, represents its content in human-readable format, often in plain text, encoded i na machine readable encoding such as ASCII or UTF-8, or in structured text based formats such as Intel Hex formats, XML, or JSON formats.
- The Immediate human readbility stands in constrast to native binary protocols which have inherent benefits for use in computer environemnts. 
- Network applications have various methods of encapsulating data. One method very common with internet protocols is a text orientated respresnetatio nthat transmitter requests and responses as lines of ASCII text, terminated by a newline character (and usually a carriage return character). Examples are FTP, SMTP, Early versions of HTTP, and the finger proocol. 
- Text-based protocols are typically optimized for human parsing and interpretationg and are therefore suitabel whenever human inspection of the protocol contents is required, such as during debuging and during early protocol development design phases.
### Binary based
- A binary protocol utilizes all values of a byte, as opposed to a text-based protocol which only uses values corresponding to human-readable characters in ASCII encoding. Binary protocols are intended to be read by a machien rather than a human being. Binary protocols have the advantage of terseness, which translates into seed of transmission and interpretation. Binary have been used in the normative documents descbing modern standards like EbXML, HTTP/2, HTTP/3,and EDOC. Additionally, an interface in UML can be considered a binary protocol. 
  
## Basic Requirements
- Gttign the data across a network is only part of the problem for a protocol. THe data receuved has to be evaluated in the context of the progress of the conversation, so a protocol must include rules describing the context. These kinds of rules are said to express the syntax of the communication. Other rules determine whether the data is meaningful for the context in which the exchange takes place. These kinds of rules are said to express the semantics of the communication.
- Messages are sent and received on communicating systemsto establish communication. Protocols should therefore specify rules governing the transmission. In geneal. much of the following is required. 
  - Data formats for data exahnge
    - Digital message bitstrings are exchanged. The bitstrings are divided in fields and each field carries information relevant to the protocol. Conceptually the bitstring is divided into two parts called the header and the payload. The actual message is carried in the payload. The header area contains the fields with relevance to the operation of the protocol. Bitstrings longer than the maximum transmission unit (MTU) are divided in pieces of appropriate size.
- Address formats for data exchange
    - Addresses are used to identify both the sender and the intended receiver(s). The addresses are carried in the header area of the bitstrings, allowing the receiver to determine whether the bitstrings are of interest and should be processed or should be ignored. A connection between a sender and a receiver can be identified using an address pair (send address, receiver address). Usually, some address values have specifical meanings. An all-1s address could be taken to mean an addressing of all stations on the network, so sending this address could result in a broadcast on the local network. The rules describing the meanings of the address values are collectively called an addressing scheme. 
- Address mapping
    - Sometimes protocols need to map addresses of one scheme on addresses of another scheme. For instance, to translate a logically IP address, specified by the application to an ethernet MAC address.
- Routing
    - when systems are not directly connected, intermediary systems along the route to the intended receiver(s) need to froward messages on behalf of the sender. On the internet, the networks are connected using routers. THe interconnection of networks throug hrouters is called internetworking. 
- Detection fo transmission errors
    - Error detection is necessary on networks where data corruption is possible. In a common approach, a CRC of the data area is added to the end of packets, makign it possible for the receiver to detect differences caused by corruption. The receiver rejects the packets on CRC differences and arranges somehow for retransmission.
- Acknolwedgements
    - Acknowledgement of correct reception of packets is required for connection-orientated comunication. Acknolwedgements are sent from receivers back to their respective senders. 
- Loss of information - timeouts and retries
    - Packets may be lost on the network or be delayed in transit. To cope with this, under some protocols, a sender may expect an Acknowledgement of correct reception from the receiver within a certain amount of time. Thus, on timeouts, the seder may need to retransmit the information. In case of a permanently broken link, the retransmission has no effect, so the number of retransmissions is limited. Exceeding  the retry limit is considered an error.
- Direction of information flow 
  - 
