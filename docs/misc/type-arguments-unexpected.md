---
title: "未預期的類型引數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32088"
  - "bc32088"
helpviewer_keywords: 
  - "BC32088"
ms.assetid: a0918e90-e7ad-4edc-81e1-584e6174bb6c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 未預期的類型引數
`Implements` 子句提供它所實作之介面成員的類型引數。  
  
 `Implements` 子句應該只會識別它所實作的介面和成員。 這表示，如果您是宣告泛型程序，則 `Of` 子句和類型引數應該會出現在宣告的主要部分中，就像您未實作介面程序一樣。  
  
 下列程式碼可能會產生此錯誤。  
  
```  
Public Interface testInterface Sub testSub(Of t)() End Interface Public Class testClass Implements testInterface Public Sub testSub() Implements testInterface.testSub(Of t)() End Sub End Class  
```  
  
 前面加上 `Implements` 子句的宣告看起來應該像介面定義，但可能加入的存取或程序修飾詞除外。 下列程式碼可避免這個錯誤。  
  
```  
Public Sub testSub(Of t)() Implements testInterface.testSub  
```  
  
 **錯誤 ID︰**BC32088  
  
### 更正這個錯誤  
  
-   從 `Implements` 子句中，移除類型引數清單。  
  
-   如果您是實作介面的泛型成員，則請將類型引數清單中放在宣告的主要部分，而且前面加上 `Implements` 關鍵字。  
  
## 請參閱  
 [Implements](../Topic/Implements%20Clause%20\(Visual%20Basic\).md)   
 [不在組建中：Implements 關鍵字和 Implements 陳述式](http://msdn.microsoft.com/zh-tw/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)