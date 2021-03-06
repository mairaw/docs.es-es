---
title: "Propiedades y argumentos | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14651389-4a49-4cbb-9ddf-c83fdc155df1
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Propiedades y argumentos
Hay varias opciones disponibles para pasar datos en una actividad.Además de utilizar <xref:System.Activities.InArgument>, las actividades también se pueden desarrollar para recibir datos utilizando las propiedades CLR estándar o las propiedades <xref:System.Activities.ActivityAction> públicas.En este tema se analiza la forma de seleccionar el tipo de método adecuado.  
  
## Utilizar propiedades CLR  
 Cuando se pasan datos en una actividad, las propiedades CLR \(es decir, los métodos públicos que utilizan rutinas Get y Set para exponer los datos\) son la opción con mayor número de restricciones.El valor de un parámetro pasado en una propiedad CLR debe conocerse cuando la solución se ha compilado; este valor será el mismo para todas las instancias del flujo de trabajo.De esta manera, un valor pasado en una propiedad CLR es similar a una constante definida en código; este valor no puede cambiar mientras dura la actividad, y no se puede cambiar para distintas instancias de la actividad.<xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A> es un ejemplo de una propiedad CLR expuesta por una actividad; el nombre del método al que la actividad llama no se puede cambiar según las condiciones del runtime y será el mismo para cada instancia de la actividad.  
  
## Utilizar argumentos  
 Se deben usar argumentos cuando los datos se evalúan solo una vez durante la duración de la actividad; es decir, su valor no cambiará durante la duración de la actividad, pero el valor puede ser diferente para distintas instancias de la actividad.<xref:System.Activities.Statements.If.Condition%2A> es un ejemplo de un valor que se evalúa una vez; por consiguiente se define como argumento.<xref:System.Activities.Statements.WriteLine.Text%2A> es otro ejemplo de un método que debe definirse como argumento, ya que se evalúa solo una vez durante la ejecución de la actividad, pero puede ser diferente para distintas instancias de la actividad.  
  
## Utilizar ActivityAction  
 Cuando es necesario evaluar los datos varias veces durante la ejecución de una actividad, debe utilizarse <xref:System.Activities.ActivityAction>.Por ejemplo, la propiedad <xref:System.Activities.Statements.While.Condition%2A> se evalúa para cada iteración del bucle <xref:System.Activities.Statements.While>.Si se utiliza <xref:System.Activities.InArgument> con este fin, nunca se saldrá del bucle, ya que el argumento no se volverá a evaluar para cada iteración y siempre se devolverá el mismo resultado.