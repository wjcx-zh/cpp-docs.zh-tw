---
title: "陣列宣告不能指定下限 | Microsoft Docs"
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
  - "vbc30805"
  - "bc30805"
helpviewer_keywords: 
  - "BC30805"
ms.assetid: f2055387-f4dc-4366-89fb-d752929a0258
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 陣列宣告不能指定下限
陣列一律以零為下限。 您可以指定零作為下限，讓您的程式碼更容易閱讀； 但無法指定任何其他值作為下限。  
  
 **錯誤 ID︰**BC30805  
  
### 更正這個錯誤  
  
-   將陣列維度設為小於項目總數的維度。 例如，`Dim y(6)` 與 `Dim x(3 To 9)` 的大小相同 \(7 個項目\)。 您也可以指定 `Dim y(0 To 6)`。  
  
-   使用位移來模擬為非零下限。 下列範例模擬 3 到 9 的維度陣列。  
  
    ```  
    Const offset As Integer = 3 Dim arrayIndex As Integer ' arrayIndex can vary between 3 and 9. Dim y(0 To 6) ' The preceding statement allocates the same number of elements ' as Dim y(3 To 9). y(arrayIndex - offset) = value ' The preceding statement converts arrayIndex to the ' corresponding index of y.  
    ```  
  
## 請參閱  
 [陣列](../Topic/Arrays%20in%20Visual%20Basic.md)   
 [Array Dimensions in Visual Basic](../Topic/Array%20Dimensions%20in%20Visual%20Basic.md)   
 [NOTINBUILD 如何：指定陣列的零下限](http://msdn.microsoft.com/zh-tw/20ffd49a-64f7-4634-8ed0-46ba1049d935)