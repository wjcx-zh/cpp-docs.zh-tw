---
title: "宣告的靜態變數 &#39;&lt;變數名稱&gt;&#39; 沒有 &#39;As&#39; 子句；假設是 &#39;Object&#39; 的類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42111"
  - "bc42111"
helpviewer_keywords: 
  - "BC42111"
ms.assetid: ca6b625c-21a5-45f7-ac67-282f6993a724
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 宣告的靜態變數 &#39;&lt;變數名稱&gt;&#39; 沒有 &#39;As&#39; 子句；假設是 &#39;Object&#39; 的類型
編譯器不會推斷靜態區域變數的資料類型。 在下列範例中，如果 `Option Strict` 設定為 `Off`，則 `m` 的類型會是 `Object` \(不論 `Option Infer` 設定為 `On` 還是 `Off`\)。 區域類型推斷不適用。  
  
```  
Sub Main() Static m = 10 End Sub  
```  
  
 根據預設，這個訊息是一個警告。 如需如何隱藏警告或如何將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42111  
  
### 解決這個警告  
  
-   指定靜態區域變數的資料類型。  
  
     例如，如果您想要上述範例中的 `m` 的類型為 `Integer`，請在宣告中指定類型。  
  
    ```  
    Sub Main() Static m As Integer = 10 End Sub  
  
    ```  
  
## 請參閱  
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)   
 [NOTINBUILD 如何：延長變數的存留期](http://msdn.microsoft.com/zh-tw/04e7c56c-1db0-4fe5-a678-859a39ec654b)   
 [Local Type Inference](../Topic/Local%20Type%20Inference%20\(Visual%20Basic\).md)   
 [Option Infer Statement](../Topic/Option%20Infer%20Statement.md)   
 [Static](../Topic/Static%20\(Visual%20Basic\).md)