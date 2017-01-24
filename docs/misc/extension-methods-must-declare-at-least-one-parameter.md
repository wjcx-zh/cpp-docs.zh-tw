---
title: "擴充方法必須宣告至少一個參數 | Microsoft Docs"
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
  - "vbc36552"
  - "bc36552"
helpviewer_keywords: 
  - "BC36552"
ms.assetid: a8cc8cdd-cdb5-42ca-b5a1-c9a71abd46eb
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 擴充方法必須宣告至少一個參數
擴充方法必須宣告至少一個參數。 第一個參數會指定要擴充的類型。  
  
 不含參數的擴充方法無效，因為第一個參數指定方法所擴充的資料類型。 第一個參數會繫結至叫用方法的資料類型執行個體。  
  
 **錯誤 ID︰**BC36552  
  
### 更正這個錯誤  
  
-   加入方法所擴充之類型的參數。  
  
## 範例  
 下列範例中的第一個參數表示 `Print` 方法可擴充 `String` 資料類型。  
  
```  
<Extension()> _ Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub  
```  
  
 如下所示呼叫擴充方法時，`str` 方法中的參數會繫結至 `greeting`，也就是呼叫 `Print` 的 `String` 執行個體。 編譯器將使用 `greeting` 作為擴充方法 `Print` 的引數。  
  
```  
Dim greeting As String = "Hello" greeting.Print()  
```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Procedure Parameters and Arguments](../Topic/Procedure%20Parameters%20and%20Arguments%20\(Visual%20Basic\).md)   
 [Procedures](../Topic/Procedures%20in%20Visual%20Basic.md)