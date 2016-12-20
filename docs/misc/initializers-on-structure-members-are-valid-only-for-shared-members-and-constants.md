---
title: "結構成員上的初始設定式只有對 &#39;Shared&#39; 成員和常數有效 | Microsoft Docs"
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
  - "bc31049"
  - "vbc31049"
helpviewer_keywords: 
  - "BC31049"
ms.assetid: 8356978e-7f84-4932-be0f-dda005c9f8ca
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 結構成員上的初始設定式只有對 &#39;Shared&#39; 成員和常數有效
結構成員變數在其宣告過程中已初始化。  
  
 **錯誤 ID︰**BC31049  
  
### 更正這個錯誤  
  
-   使用常數取代變數。  
  
-   將參數化建構函式加入結構中。 例如:  
  
    ```  
    Structure TestStruct Public t As Integer Sub New(ByVal Tval As Integer) t = Tval End Sub End Structure  
    ```  
  
## 請參閱  
 [How to: Declare a Structure](../Topic/How%20to:%20Declare%20a%20Structure%20\(Visual%20Basic\).md)   
 [Constants and Enumerations](../Topic/Constants%20and%20Enumerations%20in%20Visual%20Basic.md)