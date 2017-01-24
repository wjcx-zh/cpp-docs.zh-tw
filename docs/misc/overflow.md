---
title: "Overflow. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_OVERFLOW"
  - "vs.message.0x800A0097"
ms.assetid: 632387b9-be9c-4744-bcc5-842c45582347
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Overflow.
設定 \(Assignment\) 超過目標設定的限制。  當下列任一情形發生時，通常就會發生這個錯誤：  
  
-   設定、計算或資料型別轉換的結果過於龐大，無法在變數型別所允許的值範圍內表示。  
  
-   屬性的設定超過該屬性可接受的最大值。  
  
-   嘗試在計算時使用數字，並將數字轉換為整數，但是結果卻大於整數。  
  
### 若要更正這個錯誤  
  
1.  請將值指定給可包含較大值範圍的變數型別。  
  
     \-或\-  
  
     確認設定符合它所建立的屬性範圍。