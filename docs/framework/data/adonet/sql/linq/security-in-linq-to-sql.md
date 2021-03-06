---
title: "Seguridad en LINQ to SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Seguridad en LINQ to SQL
Siempre hay riesgos de seguridad al conectarse a una base de datos.  Aunque LINQ to SQL puede incluir algunos modos nuevos de trabajar con datos de SQL Server, no proporciona ningún mecanismo de seguridad adicional.  
  
## Control de acceso y autenticación  
 LINQ to SQL no tiene su propio modelo de usuario o sus propios mecanismos de autenticación.  Use la seguridad de SQL Server para controlar el acceso a la base de datos, las tablas de base de datos, las vistas y los procedimientos almacenados que están asignados a su modelo de objetos.  Conceda a los usuarios el acceso mínimo necesario y solicite contraseñas seguras para la autenticación de los usuarios.  
  
## Asignación e información de esquema  
 La asignación de tipos SQL\-CLR y la información de esquema de base de datos del modelo de objetos o el archivo de asignación externa está disponible para todos los usuarios que tengan acceso a esos archivos del sistema de archivos.  Asuma que la información de esquema estará disponible para todos los usuarios que tengan acceso al modelo de objetos o al archivo de asignación externa. Para impedir un acceso más extendido a la información de esquema, use mecanismos de seguridad de archivo para proteger los archivos de origen o de asignación.  
  
## Cadenas de conexión  
 Siempre que sea posible se debe evitar el uso de contraseñas en las cadenas de conexión.  No solo una cadena de conexión supone un riesgo de seguridad por derecho propio, sino que ésta se puede añadir también en texto no cifrado al modelo de objetos o al archivo de asignación externa al usar Object Relational Designer o la herramienta de línea de comandos SQLMetal.  Cualquiera que tenga acceso al modelo de objetos o al archivo de asignación externo mediante el sistema de archivos podría ver la contraseña de conexión \(si está incluida en la cadena de conexión\).  
  
 Para minimizar tales riesgos, utilice la seguridad integrada para realizar una conexión confiable con [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].  Con este enfoque no es necesario almacenar una contraseña en la cadena de conexión.  Para obtener más información, consulta [Seguridad en SQL Server](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
 Sin la seguridad integrada, se necesitará una contraseña de texto no cifrado en la cadena de conexión.  El mejor modo de ayudar a proteger la seguridad de la cadena de conexión, en lo que respecta al aumento de orden de riesgos, se detalla a continuación:  
  
-   Utilice la seguridad integrada.  
  
-   Proteja las cadenas de conexión con contraseñas y reduzca el tráfico de cadenas de conexión.  
  
-   Use una clase <xref:System.Data.SqlClient.SqlConnection?displayProperty=fullName> en lugar de una cadena de conexión dado que limita la duración de la exposición.  Se puede crear una instancia de la clase <xref:System.Data.Linq.DataContext?displayProperty=fullName> de LINQ to SQL mediante <xref:System.Data.SqlClient.SqlConnection>.  
  
-   Reduzca las duraciones y los puntos de contacto de todas las cadenas de conexión.  
  
## Vea también  
 [Información general](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)   
 [Preguntas más frecuentes](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)