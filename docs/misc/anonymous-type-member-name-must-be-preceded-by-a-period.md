---
title: "匿名類型成員名稱前面必須有一個句號 | Microsoft Docs"
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
  - "vbc36575"
  - "bc36575"
helpviewer_keywords: 
  - "BC36575"
ms.assetid: b87be29e-39f0-4830-9969-608d71137e3e
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 匿名類型成員名稱前面必須有一個句號
在匿名類型宣告的物件初始設定式清單中，指派值的新成員名稱前面必須有一個句號。 下列範例會顯示有效和無效的宣告：  
  
```vb#  
' Valid.  
Dim instanceName1 = New With {.memberName = 10}  
' Invalid declaration that causes this error.  
' Dim instanceName2 = New With {memberName = 10}  
```  
  
 **錯誤 ID︰**BC36575  
  
### 更正這個錯誤  
  
-   在成員名稱之前加上句號。  
  
## 請參閱  
 [Anonymous Types](../Topic/Anonymous%20Types%20\(Visual%20Basic\).md)