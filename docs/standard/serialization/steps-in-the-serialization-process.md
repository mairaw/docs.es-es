---
title: "Pasos del proceso de serialización"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
caps.latest.revision: 6
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: a4c125493e1b59d329bf4626c45f48b2b222d308
ms.contentlocale: es-es
ms.lasthandoff: 08/21/2017

---
# <a name="steps-in-the-serialization-process"></a>Pasos del proceso de serialización
Cuando se llama al método <xref:System.Runtime.Serialization.Formatter.Serialize*> en un [formateador](xref:System.Runtime.Serialization.Formatter), la serialización de objetos procede según la secuencia siguiente de reglas:

- Una comprobación se realiza para determinar si el formateador tiene un selector de suplente. Si el formateador lo tiene, compruebe si el selector de suplente administra objetos del tipo determinado. Si el seleccionador administra el tipo de objeto, se llama a <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=fullName> en el selector de suplente.

- Si no hay ningún selector de suplente o si no administra el tipo de objeto, se realiza una comprobación para determinar si el objeto está marcado con el atributo [Serializable](xref:System.SerializableAttribute). Si el objeto no está marcado, se genera <xref:System.Runtime.Serialization.SerializationException>.

- Si el objeto está marcado correctamente, compruebe si el objeto implementa la interfaz <xref:System.Runtime.Serialization.ISerializable>. Si es así, se llama a <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> en el objeto.
  
- Si el objeto no implementa <xref:System.Runtime.Serialization.ISerializable>, se usa la directiva de la serialización predeterminada, serializando todos los campos no marcados como [NonSerialized](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Vea también  
 [Serialización binaria](binary-serialization.md)   
 [Serialización SOAP y XML](xml-and-soap-serialization.md)
