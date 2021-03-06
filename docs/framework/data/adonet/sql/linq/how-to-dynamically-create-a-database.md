---
title: "C&#243;mo: Crear din&#225;micamente una base de datos | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# C&#243;mo: Crear din&#225;micamente una base de datos
En LINQ to SQL, se asigna un modelo de objetos a una base de datos relacional.  La asignación se habilita mediante una asignación basada en atributos o mediante un archivo de asignación externo para describir la estructura de la base de datos relacional.  En ambos escenarios, hay información suficiente sobre la base de datos relacional para crear una instancia nueva de la base de datos mediante el método <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName>.  
  
 El método <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> crea una réplica de la base de datos solo en lo que respecta a la información codificada en el modelo de objetos.  Es posible que los atributos y los archivos de asignación del modelo de objetos no codifiquen todos los elementos de la estructura de una base de datos existente.  La información de asignación no representa el contenido de las funciones definidas por el usuario, los procedimientos almacenados, los desencadenadores y las restricciones CHECK.  Este comportamiento es suficiente para varias bases de datos.  
  
 Podría utilizar el método <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> en cualquier escenario, especialmente si está disponible un proveedor de datos conocido, como Microsoft SQL Server 2008.  Entre los escenarios típicos, se pueden citar los siguientes:  
  
-   Se crea una aplicación que se instala automáticamente en un sistema del cliente.  
  
-   Se crea una aplicación cliente que necesita que una base de datos local guarde su estado sin conexión.  
  
 También puede utilizar el método <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> con SQL Server mediante un archivo .mdf o un nombre del catálogo, dependiendo de su cadena de conexión.  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utiliza la cadena de conexión para definir la base de datos que se va a crear y en qué servidor se va a crear.  
  
> [!NOTE]
>  Siempre que sea posible, utilice Windows Integrated Security para conectar con la base de datos, de modo que no se requieran contraseñas en la cadena de conexión.  
  
## Ejemplo  
 El código siguiente proporciona un ejemplo de cómo se crearía una nueva base de datos denominada MyDVDs.mdf.  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## Ejemplo  
 Puede utilizar el modelo de objetos para crear una base de datos de la manera siguiente:  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## Ejemplo  
 Cuando cree una aplicación que se instale automáticamente en un sistema de un cliente, compruebe si la base de datos existe y quítela antes de crear una nueva.  La clase <xref:System.Data.Linq.DataContext> proporciona los métodos <xref:System.Data.Linq.DataContext.DatabaseExists%2A> y <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> para ayudarle en este proceso.  
  
 En el ejemplo siguiente se muestra una manera de usar estos métodos para implementar este enfoque:  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## Vea también  
 [Asignación basada en atributos](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)   
 [Asignación externa](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)   
 [Correspondencia de tipos SQL\-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)   
 [Información general](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)   
 [Crear y enviar cambios en los datos](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)