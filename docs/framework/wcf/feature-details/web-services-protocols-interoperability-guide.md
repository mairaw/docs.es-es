---
title: "Gu&#237;a de interoperabilidad de los protocolos de servicios web | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# Gu&#237;a de interoperabilidad de los protocolos de servicios web
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementa varios protocolos de servicio web.  Muchos de estos protocolos incluyen distintas opciones y puntos de extensibilidad que son decisión del responsable de la implementación.  Este tema ofrece una lista de los protocolos de servicios web implementados por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  Otros temas incluidos en esta sección proporcionan información detallada acerca de la implementación de cada protocolo admitido.  
  
## Protocolos de servicios web implementados por WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ofrece compatibilidad con los protocolos de la infraestructura de servicios web \(WS\) a través de las características de los contratos de canales, y los protocolos de aplicación de los servicio web.  La interoperabilidad de los protocolos de aplicación se consigue mediante el lenguaje de descripción Esquema XML 1.0 \(XSD\) y el Lenguaje de descripción de servicios Web \(WSDL\) 1.1.  
  
 La interoperabilidad de los protocolos de infraestructura la proporcionan las especificaciones de WS\-\*.  Los canales de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] proporcionan compatibilidad con varios protocolos de infraestructura de WS\-\*.  Los canales de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se configuran mediante elementos de enlace.  Las tablas siguientes contienen la lista completa de los protocolos de infraestructura de WS\-\* implementados por distintos elementos de enlace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> admite las especificaciones de la tabla siguiente.  
  
|Especificación\/documento|Link|  
|-------------------------------|----------|  
|HTTP 1.1|[RFC 2616](http://go.microsoft.com/fwlink/?LinkId=90372)|  
|Enlace HTTP de SOAP 1.1|[Protocolo simple de acceso a objetos \(SOAP\) 1.1](http://go.microsoft.com/fwlink/?LinkId=90520), sección 7|  
|Enlace HTTP de SOAP 1,2|[SOAP, versión 1.2, parte 2: adjuntos \(segunda edición\)](http://go.microsoft.com/fwlink/?LinkId=95329), sección 7|  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> y <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> admiten las especificaciones de la tabla siguiente.  
  
|Especificación\/documento|Link|  
|-------------------------------|----------|  
|XML|[Lenguaje de marcado extensible \(XML\) 1.0 \(cuarta edición\)](http://go.microsoft.com/fwlink/?LinkId=15139)|  
|SOAP 1,1|[Protocolo simple de acceso a objetos \(SOAP\) 1.1](http://go.microsoft.com/fwlink/?LinkId=96687)|  
|Núcleo de SOAP 1.2|[SOAP, versión 1.2, parte 1: marco de mensajería \(segunda edición\)](http://go.microsoft.com/fwlink/?LinkId=94664)|  
|WS\-Addressing 2004\/08|[Web Services Addressing \(WS\-Addressing\)](http://go.microsoft.com/fwlink/?LinkId=81239)|  
|Web Services Addressing 1.0 de W3C \- Núcleo|[Web Services Addressing 1.0 \- Núcleo](http://go.microsoft.com/fwlink/?LinkId=96688)|  
|Web Services Addressing 1.0 de W3C \- Enlace SOAP|[Web Services Addressing 1.0 \- Enlace SOAP](http://go.microsoft.com/fwlink/?LinkId=96689)|  
|W3C Web Services Addressing 1.0 – Enlace\* WSDL|[Web Services Addressing 1.0 \- Enlace WSDL](http://go.microsoft.com/fwlink/?LinkId=96690)|  
|Metadatos de W3C Web Services Addressing 1.0|[Web Services Addressing 1.0 \- Metadatos](http://www.w3.org/TR/ws-addr-metadata/)|  
|Enlace SOAP 1.1 de WSDL|[Lenguaje de descripción de servicios Web \(WSDL\) 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)|  
|Enlace SOAP 1.2 de WSDL|[Extensión de enlace WSDL 1.1 para SOAP 1.2](http://go.microsoft.com/fwlink/?LinkId=96691)|  
  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> admite las especificaciones de la tabla siguiente.  
  
|Especificación\/documento|Link|  
|-------------------------------|----------|  
|XOP|[Empaquetado optimizado de XML binario](http://go.microsoft.com/fwlink/?LinkId=96714)|  
|MTOM \+ Enlace SOAP1.2|[Mecanismo de optimización de transmisión de mensajes SOAP](http://go.microsoft.com/fwlink/?LinkId=96713)|  
|Enlace SOAP 1.1 de MTOM|[Enlace SOAP 1.1 para MTOM 1.0](http://go.microsoft.com/fwlink/?LinkId=96712)|  
|WS\-PolicyAssertions de MTOM|Para publicación.|  
  
 <xref:System.ServiceModel.Channels.SecurityBindingElement> admite las especificaciones de la tabla siguiente.  
  
|Especificación\/documento|Link|  
|-------------------------------|----------|  
|WSS: Message Security 1,0 de SOAP|[Seguridad de servicios Web: seguridad de mensajes SOAP 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)|  
|WSS: Token Profile 1.0 de Username|[Perfil de token de nombre de usuario1.0 de seguridad de servicios Web](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> requiere Password\/@Type\=PasswordText \(de manera predeterminada\)|  
|WSS: Token Profile 1.0 de X.509|[Perfil de token de certificado X.509 de seguridad de servicios Web Services](http://go.microsoft.com/fwlink/?LinkId=95335)|  
|WSS: Token Profile 1.1 de SAML 1,0|[Seguridad de servicios Web: perfil de token de SAML](http://go.microsoft.com/fwlink/?LinkId=96693)|  
|WSS: Message Security 1.1 de SOAP|[Seguridad de servicios Web: seguridad de mensajes SOAP 1.1](http://go.microsoft.com/fwlink/?LinkId=91240)|  
|WSS: Token Profile 1.1 de Username|[Perfil de token de nombre de usuario 1.1 de seguridad de servicios Web](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> no implemente la derivación de clave basada en la contraseña;<br /><br /> requiere Password\/@Type\=PasswordText \(de manera predeterminada\)|  
|WSS: Token Profile 1.1 de X509|[Perfil de token 1.1 de certificado X.509 de seguridad de servicios Web](http://go.microsoft.com/fwlink/?LinkId=95332)|  
|WSS: Token Profile 1.1 de Kerberos|[Perfil de token de Kerberos 1.1 de servicios Web](http://go.microsoft.com/fwlink/?LinkId=95333)|  
|WSS: Token Profile 1.1 de SAML 1.1|[Perfil de token de SAML 1.1 de servicios Web](http://go.microsoft.com/fwlink/?LinkId=96694)|  
|WS\-Secure Conversation|[Lenguaje de conversión segura de servicios Web](http://go.microsoft.com/fwlink/?LinkId=95317)|  
|WS\-Trust 1.4|[Lenguaje de confianza de servicios Web](http://go.microsoft.com/fwlink/?LinkId=169514)|  
|WS\-SecurityPolicy 2005\/07|[Lenguaje de conversión segura de servicios Web](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Según la corrección de las erratas enviadas al comité técnico de OASIS WS\-SX.<br /><br /> [mensaje ws\-sx](http://go.microsoft.com/fwlink/?LinkId=96700)|  
|WS\-ReliableMessaging 1.1|[Protocolo de mensajería confiable versión 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)|  
  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> admite las especificaciones de la tabla siguiente.  
  
|Especificación\/documento|Link|  
|-------------------------------|----------|  
|WS\-Coordination|[Coordinación de servicios Web](http://go.microsoft.com/fwlink/?LinkId=95324)|  
|Transacción WS\-Atomic|[Transacción atómica de servicios Web](http://go.microsoft.com/fwlink/?LinkId=95323)|  
  
 Las clases <xref:System.ServiceModel.Description.MetadataExporter>, <xref:System.ServiceModel.Description.MetadataImporter>, <xref:System.ServiceModel.Description.WSDLExporter>, <xref:System.ServiceModel.Description.WSDLImporter> y <xref:System.ServiceModel.Description.MetadataResolver> proporcionan compatibilidad con las siguientes especificaciones de metadatos:  
  
-   [XML Schema, parte 1: estructuras \(segunda edición\)](http://go.microsoft.com/fwlink/?LinkId=3536)  
  
-   [XML Schema, parte 2: tipos de datos \(segunda edición\)](http://go.microsoft.com/fwlink/?LinkId=40138)  
  
-   [WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)  
  
-   [WS\-Policy 1.2](http://go.microsoft.com/fwlink/?LinkId=96705)  
  
-   [WS\-Policy 1.5](http://go.microsoft.com/fwlink/?LinkId=96706)  
  
-   [WS\-PolicyAttachment 1.2](http://go.microsoft.com/fwlink/?LinkId=96707)  
  
-   [WS\-MetadataExchange 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)  
  
-   [WS\-Transfer Get para la recuperación de metadatos](http://go.microsoft.com/fwlink/?LinkId=96708)  
  
 Además, en [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se implementan los siguientes perfiles de interoperabilidad:  
  
-   [Basic Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=69313)  
  
-   [Enlace SOAP simple 1.0](http://go.microsoft.com/fwlink/?LinkId=96710)  
  
-   [Basic Security Profile 1.0, borrador de trabajo](http://go.microsoft.com/fwlink/?LinkId=96711)  
  
## Vea también  
 [Protocolos de servicios Web compatibles con los enlaces de interoperabilidad proporcionados por el sistema](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)   
 [Protocolos de mensajería](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)   
 [Referencia de esquema de contrato de datos](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)   
 [WSDL y directivas](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)   
 [Protocolos de seguridad](../../../../docs/framework/wcf/feature-details/security-protocols.md)   
 [Protocolo de mensajería de confianza versión 1.0](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-0.md)   
 [Protocolo de mensajería confiable versión 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)   
 [Protocolos de transacción](../../../../docs/framework/wcf/feature-details/transaction-protocols.md)   
 [Protocolo de intercambio de contexto](../../../../docs/framework/wcf/feature-details/context-exchange-protocol.md)