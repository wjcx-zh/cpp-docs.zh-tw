---
title: "必須是 &#39;{&#39; | Microsoft Docs"
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
  - "vbc30987"
  - "bc30987"
helpviewer_keywords: 
  - "BC30987"
ms.assetid: 3d1552b6-338a-47cf-84d5-77b59209e0d3
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是 &#39;{&#39;
若要使用物件初始設定式來宣告具名或匿名類型的執行個體，您必須以大括弧 \({ 和 }\) 括住欄位或屬性清單和其初始值。  
  
```  
Dim client As New Customer() With {.Name = "Microsoft", .City = "Seattle"}  
Dim emp = New Employee() With {.Name = "Rob Young", .ID = 55555}  
Dim anon = New With {.ID = 123456}  
```  
  
 **錯誤 ID︰**BC30987  
  
### 更正這個錯誤  
  
-   請在以大括弧括住的 `With` 後面包括初始設定清單。  
  
## 請參閱  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [不在組建中：屬性程序與欄位](http://msdn.microsoft.com/zh-tw/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)   
 [Anonymous Types](../Topic/Anonymous%20Types%20\(Visual%20Basic\).md)