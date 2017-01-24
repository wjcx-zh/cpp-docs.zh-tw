---
title: "物件初始設定式語法無法用來初始化 &#39;Object&#39; 類型的執行個體 | Microsoft Docs"
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
  - "bc30994"
  - "vbc30994"
helpviewer_keywords: 
  - "BC30994"
ms.assetid: 2ef65965-f014-4fc1-8c7d-c603f0a764df
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 物件初始設定式語法無法用來初始化 &#39;Object&#39; 類型的執行個體
您無法使用物件初始設定式語法來初始化 `Object` 的執行個體。`Object` 的執行個體沒有可指派值的屬性或欄位，而且物件初始設定式語法至少需要一個這類屬性或欄位。  
  
```  
' Not valid. ' Dim obj1 = New Object With {} ' Dim obj2 = New Object With {.ToString = <some value>}  
```  
  
 **錯誤 ID︰**BC30994  
  
### 更正這個錯誤  
  
1.  宣告 `Object` 類型的執行個體，而不使用初始設定式清單：  
  
    ```  
    Dim obj3 as Object Dim obj4 as New Object()  
    ```  
  
## 請參閱  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Object Data Type](../Topic/Object%20Data%20Type.md)