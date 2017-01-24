---
title: "&#39;#ExternalSource&#39; 指示詞不可以是巢狀 | Microsoft Docs"
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
  - "bc30580"
  - "vbc30580"
helpviewer_keywords: 
  - "BC30580"
ms.assetid: 56c6ef4b-28b1-4a62-8afa-d83a7742b507
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ExternalSource&#39; 指示詞不可以是巢狀
您已嘗試將 `#ExternalSource` 指示詞放在在另一個 `#ExternalSource` 區塊內。`#ExternalSource` 指示詞參考外部程式碼，讓編譯器能夠在該程式碼中出現例外狀況時正確地回報。  
  
 `#ExternalSource` 區塊不能巢狀位於其他 `#ExternalSource` 區塊內。  
  
 **錯誤 ID︰**BC30580  
  
### 更正這個錯誤  
  
-   請將內部 `#ExternalSource` 指示詞移到結束的 `#ExternalSource` 區塊之外。  
  
## 請參閱  
 [\#ExternalSource Directive](../Topic/%23ExternalSource%20Directive.md)   
 [NOTINBUILD 條件式編譯 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)