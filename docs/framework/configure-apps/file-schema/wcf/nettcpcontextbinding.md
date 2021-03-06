---
title: "&lt;netTcpContextBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d4715e1-5fff-4c3d-a226-18f21d0b30c4
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;netTcpContextBinding&gt;
Especifica un contexto para <xref:System.ServiceModel.NetTcpBinding> que requiere que se firme el nivel de protección.  El contextExchangeMechanism para NetTcpContextBinding es SOAPHeader.  
  
## Sintaxis  
  
```  
  
<netTcpContextBinding>  
   <binding   
      closeTimeout="TimeSpan"  
            contextProtectionLevel="EncryptAndSign/None/Sign"  
      hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
      listenBacklog="Integer"  
      maxBufferPoolSize="integer"  
      maxBufferSize="Integer"  
      maxConnections="Integer"   
      maxReceivedMessageSize="Integer"  
            name="string"  
      openTimeout="TimeSpan"  
      portSharingEnabled="Boolean"  
      receiveTimeout="TimeSpan"  
      sendTimeout="TimeSpan"  
      transactionFlow="Boolean"   
      transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"   
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
  
      <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan"  
            enabled="Boolean" />  
      <security mode="Message/None/Transport/TransportWithCredential">  
           <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                realm="string"   
                defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                defaultRealm="string" />  
          <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           establishSecurityContext="Boolean"   
           negotiateServiceCredential="Boolean"/>  
       </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"   
            maxNameTableCharCount="Integer"           
            maxStringContentLength="Integer" />  
   </binding>  
</netTcpContextBinding>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|closeTimeout|Un valor <xref:System.TimeSpan> que especifica el intervalo de tiempo del que dispone una operación de cierre para completarse.  Este valor debe ser mayor o igual que <xref:System.TimeSpan.Zero>.  El valor predeterminado es 00:01:00.|  
|contextProtectionLevel|Un valor <xref:System.Net.Security.ProtectionLevel> válido que especifica el nivel de protección deseado del encabezado SOAP usado para propagar la información de contexto.  El valor predeterminado es `Sign`.|  
|hostnameComparisonMode|Especifica el modo de comparación de nombres de host HTTP usado para analizar los URI.  Este atributo es del tipo <xref:System.ServiceModel.HostnameComparisonMode>, que indica si se va a utilizar el nombre del host para llegar al servicio cuando coincida en el URI.  El valor predeterminado es <xref:System.ServiceModel.HostnameComparisonMode.StrongWildcard>, que omite el nombre del host en la coincidencia.|  
|listenBacklog|Un entero positivo que especifica el número máximo de canales que esperan ser aceptados en el agente de escucha.  Conexiones que sobrepasen este límite se pondrán a la cola hasta que quede disponible un espacio por debajo del límite.  El atributo `connectionTimeout` limita el tiempo durante el cual el cliente espera a ser conectado antes de iniciar una excepción de conexión.  El valor predeterminado es 10.|  
|maxBufferPoolSize|Entero que especifica el tamaño máximo del grupo de búferes para este enlace.  El valor predeterminado es 512 \* 1024 bytes.  En muchas partes de Windows Communication Foundation \(WCF\) se utilizan búferes.  Crear y destruir búferes cada vez que se usan es caro, y la recolección de elementos no utilizados para los búferes también es cara.  Con grupos de búferes, puede tomar un búfer del grupo, usarlo y devolverlo al grupo una vez haya terminado.  Así se evita la sobrecarga al crear y destruir búferes.|  
|maxBufferSize|Un entero positivo que especifica el tamaño máximo, en bytes, del búfer usado para almacenar los mensajes en memoria.  Si el búfer está completo, los datos excedentes permanecen en el socket subyacente hasta que el búfer tenga de nuevo espacio.  Este valor no puede ser menor que el del atributo `maxReceivedMessageSize`.  El valor predeterminado es 65536.  Para obtener más información, consulta <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|maxConnections|Un entero que especifica el número máximo de conexiones salientes y entrantes que el servicio creará\/aceptará.  Las conexiones entrantes y salientes se cuentan con respecto a un límite independiente especificado por este atributo.<br /><br /> Las conexiones entrantes que sobrepasen el límite se ponen a la cola hasta que quede disponible un espacio por debajo del límite.<br /><br /> Las conexiones salientes que sobrepasen el límite se ponen a la cola hasta que quede disponible un espacio por debajo del límite.<br /><br /> El valor predeterminado es 10.|  
|maxReceivedMessageSize|Entero positivo que especifica el tamaño máximo del mensaje, en bytes, incluidos los encabezados, que se puede recibir en un canal configurado con este enlace.  El remitente de un mensaje que supere este límite recibirá un error SOAP.  El destinatario quita el mensaje y crea una entrada del evento en el registro de seguimiento.  El valor predeterminado es 65536.|  
|name|Cadena que contiene el nombre de configuración del enlace.  Este valor debe ser único porque se usa como identificación del enlace.  A partir de [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], no es necesario que los enlaces y los comportamientos tengan nombre.  Para obtener más información sobre la configuración predeterminada, así como sobre enlaces y comportamientos sin nombre, vea [Configuración simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) y [Configuración simplificada de los servicios de WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|Valor de la estructura <xref:System.TimeSpan> que especifica el intervalo de tiempo del que dispone una operación de apertura para completarse.  Este valor debe ser mayor o igual que <xref:System.TimeSpan.Zero>.  El valor predeterminado es 00:01:00.|  
|portSharingEnabled|Valor de tipo booleano que especifica si el uso compartido de puerto TCP está habilitado para esta conexión.  Si éste es `false`, cada enlace utiliza su propio puerto exclusivo.  Este valor sólo es relevante para los servicios, porque los clientes no se ven afectados.|  
|receiveTimeout|Un valor <xref:System.TimeSpan> que especifica el intervalo de tiempo del que dispone una operación de recepción para completarse.  Este valor debe ser mayor o igual que <xref:System.TimeSpan.Zero>.  El valor predeterminado es 00:10:00.|  
|sendTimeout|Un valor <xref:System.TimeSpan> que especifica el intervalo de tiempo del que dispone una operación de envío para completarse.  Este valor debe ser mayor o igual que <xref:System.TimeSpan.Zero>.  El valor predeterminado es 00:01:00.|  
|transactionFlow|Valor booleano que especifica si el enlace admite las transacciones WS del flujo.  De manera predeterminada, es `false`.|  
|transactionProtocol|Especifica el protocolo de transacción que se va a usar con este enlace.  Los valores válidos son<br /><br /> -   OleTransactions<br />-   WSAtomicTransactionOctober2004<br /><br /> El valor predeterminado es OleTransactions.  Este atributo es del tipo <xref:System.ServiceModel.TransactionProtocol>.|  
|transferMode|Un valor <xref:System.ServiceModel.TransferMode> que especifica si los mensajes se almacenan en búfer, se transmiten o si son una solicitud o una respuesta.|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[\<seguridad\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Define la configuración de seguridad del enlace.  Este elemento es del tipo <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|Define las restricciones en la complejidad de los mensajes SOAP que pueden ser procesados por los extremos configurados con este enlace.  Este elemento es del tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/es-es/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Especifica si se establecen sesiones confiables entre los extremos del canal.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[\<enlaces\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Este elemento contiene una colección de enlaces estándar y personalizados.|  
  
## Vea también  
 <xref:System.ServiceModel.NetTcpBinding>   
 <xref:System.ServiceModel.netTcpContextBinding>   
 <xref:System.ServiceModel.Configuration.netTcpContextBindingElement>   
 <xref:System.ServiceModel.Channels.ContextBindingElement>   
 [\<netTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)   
 [Enlaces](../../../../../docs/framework/wcf/bindings.md)   
 [Configuración de enlaces proporcionados por el sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/es-es/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<enlace\>](../../../../../docs/framework/misc/binding.md)