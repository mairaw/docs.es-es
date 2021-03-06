---
title: "Expresiones no admitidas (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "ESQL"
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Expresiones no admitidas (Entity SQL)
En este tema se describen las expresiones de [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] que no se admiten en [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Para obtener más información, vea [Diferencias entre Entity SQL y Transact\-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).  
  
## Predicados cuantificados  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] permite construcciones con el formato siguiente:  
  
```  
sal > all (select salary from employees)  
sal > any (select salary from employees)  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], sin embargo, no admite tales construcciones.  En [!INCLUDE[esql](../../../../../../includes/esql-md.md)], se pueden escribir expresiones equivalentes del siguiente modo:  
  
```  
not exists(select 0 from employees as e where sal > e.salary)  
exists(select 0 from employees as e where sal > e.salary)  
```  
  
## \* \(Operador\)  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] admite el uso del operador \* en la cláusula SELECT para indicar que todas las columnas se deberían proyectar fuera.  Esto no se admite en [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## Vea también  
 [Información general de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)   
 [Diferencias entre Entity SQL y Transact\-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)