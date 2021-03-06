---
title: "UI Automation Support for the TreeItem Control Type | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control types, Tree Item"
  - "Tree Item control type"
  - "UI Automation, Tree Item control type"
ms.assetid: 229f341a-477f-434e-b877-4db9973068eb
caps.latest.revision: 22
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 22
---
# UI Automation Support for the TreeItem Control Type
> [!NOTE]
>  Esta documentación está dirigida a los desarrolladores de .NET Framework que quieran usar las clases [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] administradas definidas en el espacio de nombres <xref:System.Windows.Automation>. Para ver la información más reciente acerca de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: automatización de la interfaz de usuario](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 En este tema se ofrece información sobre la compatibilidad de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] con el tipo de control TreeItem. En [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un tipo de control es un conjunto de condiciones que un control debe cumplir para poder usar la propiedad <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>. Entre las condiciones se incluyen instrucciones específicas para la estructura de árbol [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], valores de propiedad [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] y patrones de control.  
  
 El tipo de control TreeItem representa un nodo dentro de un contenedor de árbol. Cada nodo puede contener otros nodos, llamados nodos secundarios. Los nodos primarios o los nodos que contienen nodos secundarios se pueden mostrar expandidos o contraídos.  
  
 En las secciones siguientes se definen la estructura del árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], las propiedades, los patrones de control y los eventos necesarios para el tipo de control TreeItem. Los requisitos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se aplican a todos los controles de elemento de árbol, ya sean [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] o [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## Estructura de árbol de Automatización de la interfaz de usuario necesaria  
 En la tabla siguiente se detallan la vista de control y la vista de contenido del árbol [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que pertenece a los controles de elemento de árbol y se describe lo que puede incluirse en cada vista. Para más información sobre el árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], vea [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Vista de control|Vista de contenido|  
|----------------------|------------------------|  
|TreeItem<br /><br /> -   CheckBox \(0 o 1\)<br />-   Image \(0 o 1\)<br />-   Button \(0 o 1\)<br />-   TreeItem \(0 o más\)|TreeItem<br /><br /> -   TreeItem \(0 o más\)|  
  
 Los controles de elemento de árbol pueden tener cero o más elementos secundarios de elemento de árbol en la vista de contenido del árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Si el control de elemento de árbol tiene una funcionalidad más allá de lo expuesto en los patrones de control que se muestran a continuación, el control debe basarse en el tipo de control Data Item.  
  
 Los elementos del árbol contraídos no se mostrarán en la vista de control ni en la vista de contenido hasta que estén visibles y expandidos \(o se pueden desplazar en la vista\).  
  
 La vista de control puede contener detalles adicionales de un control, entre los que se incluyen una imagen asociada o un botón. Por ejemplo, un elemento de una vista Esquema podría contener una imagen, así como un botón para expandir o contraer el esquema. Estos objetos de detalle no aparecen en la vista de contenido porque la información ya está representada por el elemento de árbol primario. Los elementos de árbol que se desplazan fuera de la pantalla aparecerán en las vistas de control y de contenido del árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] y deben tener la propiedad <xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> establecida en true.  
  
<a name="Required_UI_Automation_Properties"></a>   
## Propiedades de Automatización de la interfaz de usuario necesarias  
 En la tabla siguiente se muestran las propiedades de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que tienen valor o una definición especialmente relevante para los controles de lista. Para más información sobre las propiedades de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], vea [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Propiedad [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valor|Notas|  
|-------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Vea las notas.|El valor de esta propiedad debe ser único en todos los controles de una aplicación.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Vea las notas.|El rectángulo exterior que contiene el control completo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Vea las notas.|Esta propiedad debe devolver una ubicación del elemento que hará que el elemento cambie el estado de selección u obtenga el foco.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|TreeItem|Este valor es el mismo para todos los marcos de trabajo de la interfaz de usuario.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|El control de lista siempre se incluye en la vista de contenido del árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|El control de lista siempre se incluye en la vista de control del árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Vea las notas.|Esta propiedad se establece para indicar cuando un control de elemento de árbol se desplaza fuera de la pantalla.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Vea las notas.|Si el control puede recibir el foco del teclado, debe admitir esta propiedad.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Vea las notas.|Si el control de elemento de árbol utiliza un icono visual para indicar que es un tipo de objeto determinado, esta propiedad debe admitirse e indicar cuál es el objeto.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Los controles de elemento de árbol se etiquetan automáticamente.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"elemento de árbol"|Cadena localizada que corresponde al tipo de control TreeItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Vea las notas.|Esta propiedad expone el texto que se muestra para cada control de elemento de árbol.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## Patrones de control de Automatización de la interfaz de usuario necesarios  
 En la tabla siguiente se muestran los patrones de control de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que los controles de lista deben admitir. Para más información sobre los patrones de control, vea [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Patrón de control\/Propiedad de patrón|Compatibilidad\/Valor|Notas|  
|--------------------------------------------|---------------------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Depende|Implemente este patrón de control si el elemento de árbol tiene un comando independiente y accionable.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Sí|Todos los elementos del árbol se pueden expandir o contraer.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Expanded, Collapsed o Leaf Node|Los elementos de árbol serán nodos hoja cuando no se expandan ni contraigan.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Depende|Implemente este patrón de control si el contenedor de árbol admite el patrón de control Scroll.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Depende|Implemente este patrón de control si es posible tener una selección activa que se mantenga cuando el usuario vuelva al contenedor de árbol.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|Sí|Esta propiedad expondrá el mismo contenedor para todos los elementos de dentro del contenedor.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Depende|Implemente este patrón de control si el elemento de árbol tiene una casilla asociada.|  
  
<a name="Required_UI_Automation_Events"></a>   
## Eventos de Automatización de la interfaz de usuario necesarios  
 En la siguiente tabla se muestran los eventos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que deben admitir todos los controles de elemento de datos. Para más información sobre eventos, vea [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|Evento [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Compatibilidad|Notas|  
|----------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Requerido|Ninguna|  
|Evento de cambio de propiedad <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Obligatorio|Ninguna|  
|Evento de cambio de propiedad <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Obligatorio|Ninguna|  
|Evento de cambio de propiedad <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Obligatorio|Ninguna|  
|Evento de cambio de propiedad <xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>.|Depende|Ninguna|  
|Evento de cambio de propiedad <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>.|Obligatorio|Ninguna|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Requerido|Ninguna|  
|Evento de cambio de propiedad <xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>.|Obligatorio|Ninguno|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Depende|Ninguna|  
|Evento de cambio de propiedad <xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>.|Depende|Ninguno|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Depende|Ninguna|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Depende|Ninguna|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Depende|Ninguna|  
|Evento de cambio de propiedad <xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>.|Depende|Ninguna|  
|Evento de cambio de propiedad <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>.|Depende|Ninguno|  
  
## Vea también  
 <xref:System.Windows.Automation.ControlType.TreeItem>   
 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)   
 [UI Automation Overview](../../../docs/framework/ui-automation/ui-automation-overview.md)