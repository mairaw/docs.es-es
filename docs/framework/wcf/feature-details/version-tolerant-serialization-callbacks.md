---
title: "Devoluciones de llamadas en la serializaci&#243;n tolerante a versiones | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "OnDeserializedAttribute [WCF]"
  - "OnDeserializingAttribute [WCF]"
  - "OnSerializedAttribute [WCF]"
  - "OnSerializingAttribute [WCF]"
  - "serialization [WCF], Establecer valores predeterminados"
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# Devoluciones de llamadas en la serializaci&#243;n tolerante a versiones
El modelo de programación del contrato de datos admite totalmente los métodos de devolución de llamada de serialización tolerante a versiones que las clases <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> y <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> admiten.  
  
## Atributos tolerantes a versiones  
 Hay cuatro atributos de devolución de llamada.Cada atributo se puede aplicar a un método que el motor de serialización\/deserialización denomina en varios momentos.La siguiente tabla explica cuándo utilizar cada atributo.  
  
|Atributo|Cuando se llama al método correspondiente|  
|--------------|-----------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Llamado antes de serializar el tipo.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Llamado después de serializar el tipo.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Llamado antes de deserializar el tipo.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Llamado después de deserializar el tipo.|  
  
 Los métodos deben aceptar un parámetro <xref:System.Runtime.Serialization.StreamingContext>.  
  
 Estos métodos están pensados principalmente para utilizarlos con controlador de versiones o inicialización.No se llama a ningún constructor durante la deserialización.Por lo tanto, puede que no se puedan inicializar correctamente los miembros de datos \(en valores predeterminados intencionales\), si los datos de estos miembros faltan en la secuencia de entrada, por ejemplo, si los datos proceden de una versión anterior de un tipo al cual le faltan algunos miembros de datos. Para corregirlo, utilice el método de devolución de llamada marcado con <xref:System.Runtime.Serialization.OnDeserializingAttribute>, tal y como se muestra en el siguiente ejemplo.  
  
 Puede marcar sólo un método por tipo con cada uno de los atributos de devolución de llamada anteriores.  
  
### Ejemplo  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## Vea también  
 <xref:System.Runtime.Serialization.OnSerializingAttribute>   
 <xref:System.Runtime.Serialization.OnSerializedAttribute>   
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>   
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>   
 <xref:System.Runtime.Serialization.StreamingContext>   
 [Serialización tolerante a versiones](../../../../docs/framework/serialization/version-tolerant-serialization.md)