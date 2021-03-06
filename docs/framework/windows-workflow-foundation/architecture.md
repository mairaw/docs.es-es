---
title: "Arquitectura de Windows Workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# Arquitectura de Windows Workflow
[!INCLUDE[wf](../../../includes/wf-md.md)] genera el nivel de abstracción para desarrollar aplicaciones interactivas de ejecución prolongada.Las unidades de trabajo se encapsulan como actividades.Las actividades se ejecutan en un entorno que proporcione los medios para el control de flujo, el control de excepciones, la propagación de errores, la persistencia de los datos de estado, la carga y descarga de flujos de trabajo en progreso de la memoria, el seguimiento y el flujo de la transacción.  
  
## Arquitectura de la actividad  
 Las actividades se desarrollan como tipos CLR que derivan de <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> o <xref:System.Activities.NativeActivity>, o sus variantes que devuelven un valor, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601> o <xref:System.Activities.NativeActivity%601>.Desarrollar actividades que derivan de <xref:System.Activities.Activity> permite al usuario ensamblar actividades existentes previamente para crear rápidamente las unidades de trabajo que se ejecutan en el entorno del flujo de trabajo.<xref:System.Activities.CodeActivity>, por otro lado, permite crear la lógica de ejecución en código administrado usando principalmente <xref:System.Activities.CodeActivityContext> para el acceso a los argumentos de actividad.<xref:System.Activities.AsyncCodeActivity> es similar a <xref:System.Activities.CodeActivity> salvo que puede usarse para implementar tareas asincrónicas.Desarrollar actividades que derivan de <xref:System.Activities.NativeActivity> permite a los usuarios tener acceso al runtime a través de <xref:System.Activities.NativeActivityContext> para funciones como la programación de elementos secundarios, la creación de marcadores, invocar el trabajo asincrónico, el registro de transacciones y mucho más.  
  
 La creación de actividades que derivan de <xref:System.Activities.Activity> es declarativo. Estas actividades se pueden crear en XAML.En el siguiente ejemplo, una actividad llamada `Prompt` se crea usando otras actividades para el cuerpo de ejecución.  
  
```  
<Activity x:Class='Prompt'  
  xmlns:x='http://schemas.microsoft.com/winfx/2006/xaml'  
    xmlns:z='http://schemas.microsoft.com/netfx/2008/xaml/schema'  
xmlns:my='clr-namespace:XAMLActivityDefinition;assembly=XAMLActivityDefinition'  
xmlns:s="clr-namespace:System;assembly=mscorlib"  
xmlns="http://schemas.microsoft.com/2009/workflow">  
<z:SchemaType.Members>  
    <z:SchemaType.SchemaProperty Name='Text' Type=' InArgument(s:String)' />  
  <z:SchemaType.SchemaProperty Name='Response' Type='OutArgument(s:String)' />  
</z:SchemaType.Members>  
  <Sequence>  
    <my:WriteLine Text='[Text]' />  
    <my:ReadLine BookmarkName='r1' Result='[Response]' />  
  </Sequence>  
</Activity>  
```  
  
## Contexto de actividad  
 <xref:System.Activities.ActivityContext> es la interfaz del autor de la actividad en el tiempo de ejecución del flujo de trabajo y proporciona acceso a la amplia variedad de características del tiempo de ejecución.En el siguiente ejemplo, se define una actividad que usa el contexto de ejecución para crear un marcador \(el mecanismo que permite a una actividad registrar un punto de continuación en su ejecución y que puede reanudarse mediante el paso de datos a la actividad por parte de un host\).  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## Ciclo de vida de la actividad  
 La instancia de una actividad empieza en el estado <xref:System.Activities.ActivityInstanceState>.A menos que se encuentren excepciones, permanece en este estado hasta que todas las actividades secundarias se hayan terminado de ejecutar y se hayan completado otros trabajos pendientes \(objetos <xref:System.Activities.Bookmark>, por ejemplo\). Una vez llegado este punto, cambia al estado <xref:System.Activities.ActivityInstanceState>.El elemento primario de una instancia de actividad puede solicitar la cancelación de un elemento secundario; si el elemento secundario puede cancelarse, se completa en el estado <xref:System.Activities.ActivityInstanceState>.Si se produce una excepción durante la ejecución, el runtime coloca la actividad en el estado <xref:System.Activities.ActivityInstanceState> y propaga la excepción hasta la cadena primaria de actividades.A continuación se describen tres estados de realización de una actividad:  
  
-   **Cerrado:** la actividad ha completado su trabajo y ha salido.  
  
-   **Cancelado:** la actividad ha abandonado su trabajo sin contratiempos y ha salido.En este estado, el trabajo no se revierte de manera explícita.  
  
-   **Con errores:** la actividad ha encontrado un error y ha salido sin completar su trabajo.  
  
 Las actividades permanecen en el estado <xref:System.Activities.ActivityInstanceState> cuando se conservan o descargan.