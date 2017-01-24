---
title: "在 &#39;&lt;模組名稱&gt;&#39; 中定義的擴充方法 &#39;&lt;方法名稱&gt;&#39; 不是泛型 (或沒有不受限的類型參數)，因此不可有類型引數 | Microsoft Docs"
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
  - "bc36907"
  - "vbc36907"
helpviewer_keywords: 
  - "BC36907"
ms.assetid: 45191e93-89d1-48ec-99a5-ff9661a2a6ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在 &#39;&lt;模組名稱&gt;&#39; 中定義的擴充方法 &#39;&lt;方法名稱&gt;&#39; 不是泛型 (或沒有不受限的類型參數)，因此不可有類型引數
在擴充方法的呼叫中已指定類型引數，而擴充方法沒有泛型參數或沒有未指定類型的泛型參數。 例如，下列程式碼會造成這個錯誤。  
  
```vb#  
' The extension method is not generic. <Extension()> _ Sub Example(ByVal str As String) ' Body of the Sub. End Sub  
```  
  
```vb#  
Dim str = "hi" '' The call to Example specifies a type argument. '' Not valid. 'str.Example(Of String)()  
```  
  
 **錯誤 ID︰**BC36907  
  
### 更正這個錯誤  
  
-   在擴充方法定義中加入類型參數。  
  
-   移除程序呼叫中的額外類型引數。  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)