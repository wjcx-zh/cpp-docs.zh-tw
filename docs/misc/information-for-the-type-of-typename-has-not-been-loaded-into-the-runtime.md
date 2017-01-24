---
title: "類型 &#39;&lt;類型名稱&gt;&#39; 的資訊尚未在執行階段中載入 | Microsoft Docs"
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
  - "vbc30750"
  - "bc30750"
helpviewer_keywords: 
  - "BC30750"
ms.assetid: b0f074f9-571d-48f8-b334-4fd34b61cd89
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型 &#39;&lt;類型名稱&gt;&#39; 的資訊尚未在執行階段中載入
參考了執行階段尚未載入的類型。  
  
 **錯誤 ID︰**BC30750  
  
### 更正這個錯誤  
  
1.  請重組您的程式碼，以在目前範圍內定義類型。  
  
2.  請確認已定義成員，而且成員名稱拼字正確。  
  
3.  嘗試存取模組中所宣告的其中一個成員。 在某些情況下，偵錯環境找不到成員，因為未載入宣告它們的模組。  
  
## 請參閱  
 [Visual Studio 偵錯](../Topic/Debugging%20in%20Visual%20Studio.md)