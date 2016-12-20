---
title: "Command requires one argument. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INCORRECTPARAMCOUNT1"
  - "vs.message.0x800A00C3"
ms.assetid: b4d98e6d-6970-42fb-b1de-43f2e952fb9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Command requires one argument.
當輸入給命令的資訊不足或使用不正確的引數組合時，通常就會發生這個錯誤。  
  
 例如，為 `alias` 命令輸入 `alias` `/delete sample1 sample2`，就會顯示此錯誤，因為別名 `/delete` 只能使用一個別名名稱，而非兩個。  別名名稱並不包含空格，因此 \[尋找\/命令\] 方塊和 \[命令\] 視窗將 `sample1 sample2` 解譯為兩個不同的別名名稱。  
  
### 若要更正這個錯誤  
  
1.  請檢查文件中命令的正確語法，然後再試一次。  
  
## 請參閱  
 [Visual Studio 命令](../Topic/Visual%20Studio%20Commands.md)