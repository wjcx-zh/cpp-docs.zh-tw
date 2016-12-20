---
title: "&#39;#End ExternalSource&#39; 之前必須搭配相對應的 &#39;#ExternalSource&#39; | Microsoft Docs"
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
  - "bc30578"
  - "vbc30578"
helpviewer_keywords: 
  - "BC30578"
ms.assetid: f011673d-eced-46a7-a08e-d54d86c8a76b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#End ExternalSource&#39; 之前必須搭配相對應的 &#39;#ExternalSource&#39;
`#ExternalSource` 指示詞參考外部程式碼，讓編譯器能夠在該程式碼中出現例外狀況時正確地回報。`#ExternalSource` 區塊必須以 `#ExternalSource` 開頭並以 `#End ExternalSource` 結尾。  
  
 **錯誤 ID︰**BC30578  
  
### 更正這個錯誤  
  
1.  請將 `#ExternalSource` 加入您程式碼中的適當位置。  
  
2.  如果不需要則請移除 `#End ExternalSource`。  
  
## 請參閱  
 [\#ExternalSource Directive](../Topic/%23ExternalSource%20Directive.md)   
 [NOTINBUILD 條件式編譯 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)