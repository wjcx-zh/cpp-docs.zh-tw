---
title: "無法從包含 &#39;&lt;變數名稱&gt;&#39; 的運算式推斷 &#39;&lt;變數名稱&gt;&#39; 的類型 | Microsoft Docs"
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
  - "vbc30980"
  - "bc30980"
helpviewer_keywords: 
  - "BC30980"
ms.assetid: 43a5d008-5362-481b-845b-b9bb00a61a83
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法從包含 &#39;&lt;變數名稱&gt;&#39; 的運算式推斷 &#39;&lt;變數名稱&gt;&#39; 的類型
如果變數用於在宣告中建立其初始值，則編譯器無法推斷變數的資料類型。  
  
 例如，如果 `Option Infer` 設定為 `On`，則下列範例不會編譯：  
  
-   宣告  
  
    ```  
    ' Does not compile with Option Infer on. Dim m = m Dim d = someFunction(d)  
    ```  
  
-   `For`  迴圈  
  
    ```  
    ' Does not compile with Option Infer on. For j = 1 To j Next  
    ```  
  
-   `For Each`  迴圈  
  
    ```  
    ' Does not compile with Option Infer on. For Each customer In customer.Orders Next  
    ```  
  
 **錯誤 ID︰**BC30980  
  
### 更正這個錯誤  
  
-   如果兩個變數是要用來參考不同的值，請變更您所宣告變數的名稱。  
  
-   在指派的右側，使用常值，而非初始值中的變數名稱。  
  
-   使用 `As` 子句來指定所宣告變數的類型：  
  
## 請參閱  
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)   
 [For Each...Next 陳述式](../Topic/For%20Each...Next%20Statement%20\(Visual%20Basic\).md)   
 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)   
 [Local Type Inference](../Topic/Local%20Type%20Inference%20\(Visual%20Basic\).md)   
 [Option Infer Statement](../Topic/Option%20Infer%20Statement.md)