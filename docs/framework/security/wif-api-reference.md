---
title: Referencia de API de WIF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
caps.latest.revision: 4
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ef439ff502fc39074d36f63d139fd23e42471d42
ms.contentlocale: es-es
ms.lasthandoff: 08/21/2017

---
# <a name="wif-api-reference"></a>Referencia de API de WIF
Las clases de Windows Identity Foundation (WIF) se dividen entre los siguientes ensamblados: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll) y `System.ServiceModel` (System.ServiceModel.dll). Este tema proporciona vínculos a los espacios de nombres de WIF e incluye breves explicaciones de las clases que contiene cada espacio de nombres.  
  
> [!IMPORTANT]
>  Los siguientes espacios de nombres `System.IdentityModel` contienen clases que implementan el modelo de identidad basado en notificaciones de WCF: <xref:System.IdentityModel.Claims?displayProperty=fullName>, <xref:System.IdentityModel.Policy?displayProperty=fullName> y <xref:System.IdentityModel.Selectors?displayProperty=fullName>. A partir de .NET Framework 4.5, el modelo de identidad basado en notificaciones de WCF se reemplaza por WIF. No debe utilizar clases en estos tres espacios de nombres cuando compile soluciones basadas en WIF.  
  
 <xref:System.IdentityModel?displayProperty=fullName>  
 Contiene clases que representan las transformaciones de cookies, los servicios de token de seguridad y los lectores de diccionario XML especializados.  
  
 <xref:System.IdentityModel.Configuration?displayProperty=fullName>  
 Contiene clases que proporcionan la configuración para las aplicaciones y los servicios creados con Windows Identity Foundation (WIF). Las clases de este espacio de nombres representan la configuración del elemento [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md).  
  
 <xref:System.IdentityModel.Metadata?displayProperty=fullName>  
 Contiene clases que representan los elementos de un documento de metadatos de federación.  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName>  
 Contiene clases que representan artefactos de WS-Trust.  
  
 <xref:System.IdentityModel.Services?displayProperty=fullName>  
 Contiene clases que se usan en escenarios pasivos (WS-Federation). También contiene algunas clases que representan la configuración del elemento [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md). La configuración de este elemento configura WS-Federation para las aplicaciones. El espacio de nombres `System.IdentityModel.Services.Configuration` contiene la mayoría de las clases que se usan para configurar WS-Federation.  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>  
 Contiene clases que proporcionan la configuración para las aplicaciones de WIF que usan el protocolo WS-Federation. Las clases de este espacio de nombres representan la configuración del elemento [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md). El espacio de nombres `System.IdentityModel.Services` además contiene algunas clases que se usan para configurar WS-Federation.  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=fullName>  
 Contiene controladores de tokens de seguridad especializados para escenarios de granja de servidores web.  
  
 <xref:System.IdentityModel.Tokens?displayProperty=fullName>  
 Contiene clases que representan tokens de seguridad, controladores de tokens de seguridad y otros artefactos de tokens de seguridad.  
  
 <xref:System.Security.Claims?displayProperty=fullName>  
 Contiene clases que representan notificaciones, identidades basadas en notificaciones, entidades de seguridad basadas en notificaciones y otros artefactos del modelo de identidad basado en notificaciones.  
  
 <xref:System.ServiceModel.Security?displayProperty=fullName>  
 Contiene clases que representan contratos de WCF, canales, hosts de servicio y otros artefactos que se usan en escenarios activos (WS-Trust). Este espacio de nombres además contiene clases que son específicas de Windows Communication Foundation (WCF) y que WIF no usa.  
  
## <a name="see-also"></a>Vea también  
 [WIF Configuration Reference (Referencia de configuración de WIF)](../../../docs/framework/security/wif-configuration-reference.md)   
 [Asignación de espacio de nombres entre WIF 3.5 y WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)

