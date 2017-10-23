# Network

## Concepts

* IMEI (international mobile equipment identity)
* IMSI (international mobile sbuscriber identity)
* ICCID (Integrate circuit card identity)
* Mac Address
* OSI Model (Open System Interconnect)
* TCP/IP model(Transmission Control Protocol / Internet Protocol)
  TCP/IP model is a simplification of OSI Model
  Protocol runing on TCP/IP are stateless, but TCP itself is not stateless
* GSM vs GPRS 
  GSM is for 2G network

  **what happens are press google.com?** [answer](http://blog.csdn.net/dojiangv/article/details/51794535)
  1. url -> IP address by browser/DNS
  2. browser oepn TCP connection(three way handshake)
  3. send http request through TCP connection
  4. Recied HTTP response. 
  5. Browser cache
  6. Delivery page

 - WebService [reference](http://blog.csdn.net/wooshn/article/details/8069087/)
    WebService是一种跨编程语言和跨操作系统平台的远程调用技术
    XML+XSD,SOAP和WSDL就是构成WebService平台的三大技术
    SOAP协议 = HTTP协议 + XML数据格式
    WSDL(Web Services Description Language)就是这样一个基于XML的语言，用于描述Web Service及其函数、参数和返回值。相对于一个说明文件

 - SOA (Service-oriented Architecture)