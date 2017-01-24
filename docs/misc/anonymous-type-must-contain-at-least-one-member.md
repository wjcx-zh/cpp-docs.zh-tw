---
title: "匿名類型至少必須包含一個成員 | Microsoft Docs"
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
  - "bc36574"
  - "vbc36574"
helpviewer_keywords: 
  - "BC36574"
ms.assetid: fdc8dd47-ea38-49e8-8dd5-676f726cd101
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 匿名類型至少必須包含一個成員
匿名類型宣告中的初始設定式清單不可為空白。  
  
```  
' Not valid. ' Dim anonInstance = New With {}  
```  
  
 **錯誤 ID︰**BC36574  
  
### 更正這個錯誤  
  
-   在大括號內宣告一個成員，如下列程式碼所示。  
  
    ```  
    Dim anonInstance = New With {.MemberName = "value"}  
    ```  
  
## 請參閱  
 [Anonymous Types](../Topic/Anonymous%20Types%20\(Visual%20Basic\).md)