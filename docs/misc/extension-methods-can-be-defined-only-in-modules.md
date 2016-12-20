---
title: "擴充方法只能定義於模組中 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36551"
  - "bc36551"
helpviewer_keywords: 
  - "BC36551"
ms.assetid: c832d523-5bf6-4baf-b91c-bd26d94453ed
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 擴充方法只能定義於模組中
如果已在模組外部定義擴充方法，就會發生這個錯誤。 在 Visual Basic 中，必須在標準模組內定義所有擴充方法。  
  
 **錯誤 ID︰**BC36551  
  
### 更正這個錯誤  
  
-   請將擴充方法放在模組中。  
  
## 範例  
 下列範例透過加入 `Print` 方法來擴充 `String` 類別。  
  
```  
Imports StringUtility Imports System.Runtime.CompilerServices Namespace StringUtility <Extension()> _ Module StringExtensions <Extension()> _ Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub End Module End Namespace  
```  
  
## 請參閱  
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Module \<keyword\>](../Topic/Module%20%3Ckeyword%3E%20\(Visual%20Basic\).md)   
 [Module Statement](../Topic/Module%20Statement.md)