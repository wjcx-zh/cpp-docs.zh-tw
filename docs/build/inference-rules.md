---
title: "推斷規則 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NMAKE 中的推斷規則"
  - "NMAKE 程式, 推斷規則"
  - "規則, 推斷"
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 推斷規則
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

推斷規則提供命令以更新目標，並推斷目標的相依性。  推斷規則中的副檔名與具有相同主檔名的單一目標和相依性相符。  推斷規則為使用者定義或預先定義；可以重新定義預先定義的規則。  
  
 如果過時的相依性沒有命令，且如果 [.SUFFIXES](../build/dot-directives.md) 包含有相依性的副檔名，NMAKE 會使用副檔名與目前或指定目錄中的目標和現有檔案相符的規則。  如果有一個以上的規則符合現有檔案，**.SUFFIXES** 清單會決定要使用哪一個；清單的優先順序是由左到右遞減。  如果相依檔案不存在，且沒有在另一個描述區塊中列為目標，推斷規則可從具有相同主檔名的其他檔案中建立所遺失的相依性。  如果描述區塊的目標沒有相依性或命令，推斷規則可以更新目標。  即是描述區塊不存在，推斷規則仍可建置命令列目標。  即使指定了明確相依性，NMAKE 仍可叫用推斷相依的規則。  
  
## 您還想知道關於哪些方面的詳細資訊？  
 [定義規則](../build/defining-a-rule.md)  
  
 [批次模式規則](../build/batch-mode-rules.md)  
  
 [預先定義的規則](../build/predefined-rules.md)  
  
 [推斷相依和規則](../build/inferred-dependents-and-rules.md)  
  
 [推斷規則的優先順序](../build/precedence-in-inference-rules.md)  
  
## 請參閱  
 [NMAKE 參考](../build/nmake-reference.md)