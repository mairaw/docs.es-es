---
title: "&lt;ws2007HttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;ws2007HttpBinding&gt;
Define un enlace interoperable que proporciona compatibilidad para las versiones correctas de los elementos de enlace <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, y <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A>.  
  
## Sintaxis  
  
```  
  
<ws2007HttpBinding>  
    <binding   
        allowCookies="Boolean"  
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"  
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
  
textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
        <security mode="Message/None/Transport/TransportWithCredential">  
           <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                realm="string"   
                                />  
          <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"  
           negotiateServiceCredential="Boolean"  
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
</ws2007HttpBinding>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`allowCookies`|Un valor que indica si el cliente acepta las cookies y las propaga en solicitudes futuras.  De manera predeterminada, es `false`.<br /><br /> Puede utilizar esta propiedad al interactuar con los servicios Web ASP.NET \(ASMX\) que utilizan cookies.  Esto garantiza que las cookies que el servidor devuelve se copian automáticamente en todas las solicitudes futuras de cliente para ese servicio.|  
|`bypassProxyOnLocal`|Un valor que indica si se omitirá el servidor proxy para las direcciones locales.  De manera predeterminada, es `false`.|  
|`closeTimeout`|Un valor <xref:System.TimeSpan> que especifica el intervalo de tiempo del que dispone una operación de cierre para completarse.  Este valor debe ser mayor o igual que <xref:System.TimeSpan.Zero>.  El valor predeterminado es 00:01:00.|  
|`hostnameComparisonMode`|Especifica el modo de comparación del nombre del host HTTP usado para analizar los URI \(Uniform Resource Identifier\).  Este atributo es del tipo <xref:System.ServiceModel.HostnameComparisonMode>, que indica si se va a utilizar el nombre del host para llegar al servicio cuando coincida en el URI.  El valor predeterminado es <xref:System.ServiceModel.HostnameComparisonMode.StrongWildcard>, que omite el nombre del host en la coincidencia.|  
|`maxBufferPoolSize`|El tamaño máximo del grupo de búferes para este enlace.  El valor predeterminado es 524.288 bytes \(512 × 1.024\).  Muchas partes de búferes de uso [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  Crear y destruir búferes cada vez que se usan es caro, como lo es la recolección de elementos no utilizados para los búferes.  Con los grupos de búferes, puede tomar un búfer del grupo, usarlo y devolverlo al grupo una vez haya terminado.  Esto evita la sobrecarga al crear y destruir búferes.|  
|`maxReceivedMessageSize`|El tamaño máximo del mensaje, en bytes, incluidos los encabezados, que puede recibir un canal configurado con este enlace.  El remitente de un mensaje que supere este límite recibe un error SOAP.  El destinatario quita el mensaje y crea una entrada del evento en el registro de seguimiento.  El valor predeterminado es 65536.|  
|`messageEncoding`|Define el codificador utilizado para codificar el mensaje.  Los valores válidos son los siguientes:<br /><br /> -   `Text`: Utilice un codificador de mensajes de texto.<br />-   `Mtom`: Utilice un codificador del Mecanismo de optimización de transmisión de mensajes 1.0 \(MTOM\).<br /><br /> De manera predeterminada, es `Text`.<br /><br /> Este atributo es del tipo <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Nombre de configuración del enlace.  Este valor debe ser único porque se usa como identificación del enlace.  A partir de [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], no es necesario que los enlaces y los comportamientos tengan nombre.  Para obtener más información sobre la configuración predeterminada, así como sobre enlaces y comportamientos sin nombre, vea [Configuración simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) y [Configuración simplificada de los servicios de WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|Valor de la estructura <xref:System.TimeSpan> que especifica el intervalo de tiempo del que dispone una operación de apertura para completarse.  Este valor debe ser mayor o igual que <xref:System.TimeSpan.Zero>.  El valor predeterminado es 00:01:00.|  
|`proxyAddress`|Un URI que especifica la dirección del proxy HTTP.  Si `useSystemWebProxy` es `true`, este valor debe ser `null`.  De manera predeterminada, es `null`.|  
|`receiveTimeout`|Un valor <xref:System.TimeSpan> que especifica el intervalo de tiempo del que dispone una operación de recepción para completarse.  Este valor debe ser mayor o igual que <xref:System.TimeSpan.Zero>.  El valor predeterminado es 00:01:00.|  
|`sendTimeout`|Un valor <xref:System.TimeSpan> que especifica el intervalo de tiempo del que dispone una operación de envío para completarse.  Este valor debe ser mayor o igual que <xref:System.TimeSpan.Zero>.  El valor predeterminado es 00:01:00.|  
|`textEncoding`|Especifica el codificador del juego de caracteres que se va a usar para emitir los mensajes en el enlace.  Los valores válidos son los siguientes:<br /><br /> -   `UnicodeFffeTextEncoding`: Codificación Unicode Big Endian.<br />-   `Utf16TextEncoding`: Codificación de 16 bits.<br />-   `Utf8TextEncoding`: Codificación de 8 bits.<br /><br /> De manera predeterminada, es `Utf8TextEncoding`.<br /><br /> Este atributo es del tipo <xref:System.Text.Encoding>.|  
|`transactionFlow`|Valor que especifica si el enlace admite el flujo de transacciones de WS.  De manera predeterminada, es `false`.|  
|`useDefaultWebProxy`|Un valor que especifica si se utiliza el proxy HTTP del sistema configurado automáticamente.  De manera predeterminada, es `true`.|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[\<seguridad\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Define la configuración de seguridad del enlace.  Este elemento es del tipo <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|Obtiene las restricciones de la complejidad de los mensajes SOAP que pueden procesar los extremos configurados con este enlace.  Este elemento es del tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/es-es/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Especifica si se establecen sesiones confiables entre los extremos del canal.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[\<enlaces\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Este elemento contiene una colección de enlaces estándar y personalizados.|  
  
## Comentarios  
 `WS2007HttpBinding` agrega el enlace proporcionado por un sistema similar a `WSHttpBinding` pero usa las versiones estándar de la Organización para el avance de estándares de información estructurada \(OASIS, Organization for the Advancement of Structured Information Standards\) de los protocolos ReliableSession, Security y TransactionFlow.  Se requiere ningún cambio en el modelo de objetos o la configuración predeterminada cuando se utilice este enlace.  
  
## Ejemplo  
  
```  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <ws2007HttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"  
                    sendTimeout="00:00:40"  
                    bypassProxyOnLocal="false"  
                    transactionFlow="false"   
                    hostNameComparisonMode="WeakWildcard"  
                    maxReceivedMessageSize="1000"  
                    messageEncoding="Mtom"   
                    proxyAddress="http://www.contoso.com"  
                    textEncoding="utf-16"  
                    useDefaultWebProxy="false">  
                    <reliableSession ordered="false"  
                         inactivityTimeout="00:02:00"  
                         enabled="true" />  
                    <security mode="Transport">  
                         <transport clientCredentialType="Digest"  
                            proxyCredentialType="None"  
                            realm="someRealm" />  
                         <message clientCredentialType="Windows"  
                            negotiateServiceCredential="false"  
                            algorithmSuite="Aes128"   
                            defaultProtectionLevel="None" />  
                    </security>  
                </binding>  
           </ws2007HttpBinding>  
        </bindings>  
    </system.ServiceModel>  
</configuration>  
```  
  
## Vea también  
 <xref:System.ServiceModel.WS2007HttpBinding>   
 <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>   
 [Enlaces](../../../../../docs/framework/wcf/bindings.md)   
 [Configuración de enlaces proporcionados por el sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/es-es/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<enlace\>](../../../../../docs/framework/misc/binding.md)