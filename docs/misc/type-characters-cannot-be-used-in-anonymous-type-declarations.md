---
title: "匿名類型宣告中不能使用類型字元 | Microsoft Docs"
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
  - "bc36560"
  - "vbc36560"
helpviewer_keywords: 
  - "BC36560"
ms.assetid: 70eee559-d6fc-409b-b835-2c84511b160e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 匿名類型宣告中不能使用類型字元
當您宣告匿名類型的執行個體時，無法使用屬性名稱的類型字元。 屬性的資料類型是從指派給它的值推斷而來。 例如，下列宣告無效。  
  
```vb#  
'' Not valid. 'Dim anon1 = New With {.ID$ = "abc"} 'Dim anon2 = New With {.ID$ = 42}  
```  
  
 **錯誤 ID︰**BC36560  
  
### 更正這個錯誤  
  
-   從初始設定式清單中移除類型字元。 如果建立您要用於屬性的資料類型時需要明確地轉換指派的值，則請這麼做。  
  
    ```vb#  
    ' Valid. Dim anon1 = New With {.ID = "abc"} Dim anon2 = New With {.ID = CStr(42)}  
    ```  
  
## 請參閱  
 [Anonymous Types](../Topic/Anonymous%20Types%20\(Visual%20Basic\).md)   
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)   
 [Implicit and Explicit Conversions](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)