---
title: "Cómo: ordenar o filtrar los datos de texto por palabra o campo (LINQ) (Visual Basic) | Documentos de Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 541da47893217e2915a6b001d1141eaadfa9e9e8
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a>Cómo ordenar o filtrar datos de texto por palabra o campo (LINQ) (Visual Basic)
En el ejemplo siguiente se muestra cómo ordenar líneas de texto estructurado, como valores separados por comas, por cualquier campo de la línea. El campo se puede especificar dinámicamente en tiempo de ejecución. Supongamos que los campos de scores.csv representan el número de identificador de un estudiante, seguido de una serie de cuatro puntuaciones.  
  
### <a name="to-create-a-file-that-contains-data"></a>Para crear un archivo que contiene los datos  
  
1.  Copiar los datos de scores.csv del tema [Cómo: unir contenido de archivos no similares (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) y guárdelo en la carpeta de su solución.  
  
## <a name="example"></a>Ejemplo  
  
```vb  
Class SortLines  
  
    Shared Sub Main()  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' Change this to any value from 0 to 4  
        Dim sortField As Integer = 1  
  
        Console.WriteLine("Sorted highest to lowest by field " & sortField)  
  
        ' Demonstrates how to return query from a method.  
        ' The query is executed here.  
        For Each str As String In SortQuery(scores, sortField)  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    Shared Function SortQuery(  
        ByVal source As IEnumerable(Of String),   
        ByVal num As Integer) As IEnumerable(Of String)  
  
        Dim scoreQuery = From line In source   
                         Let fields = line.Split(New Char() {","})   
                         Order By fields(num) Descending   
                         Select line  
  
        Return scoreQuery  
    End Function  
End Class  
' Output:  
' Sorted highest to lowest by field 1  
' 116, 99, 86, 90, 94  
' 120, 99, 82, 81, 79  
' 111, 97, 92, 81, 60  
' 114, 97, 89, 85, 82  
' 121, 96, 85, 91, 60  
' 122, 94, 92, 91, 91  
' 117, 93, 92, 80, 87  
' 118, 92, 90, 83, 78  
' 113, 88, 94, 65, 91  
' 112, 75, 84, 91, 39  
' 119, 68, 79, 88, 92  
' 115, 35, 72, 91, 70  
```  
  
 En este ejemplo también muestra cómo devolver una variable de consulta de una función.  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Crear un proyecto destinado a .NET Framework versión 3.5 o posterior con una referencia a System.Core.dll y una `Imports` instrucción del espacio de nombres System.Linq.  
  
## <a name="see-also"></a>Vea también  
 [LINQ y cadenas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
