---
title: "屬性建構函式的 &#39;ByRef&#39; 參數類型為 &#39;&lt;類型名稱&gt;&#39;；不可以使用具有 byref 參數的建構函式來套用屬性 | Microsoft Docs"
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
  - "bc36006"
  - "vbc36006"
helpviewer_keywords: 
  - "BC36006"
ms.assetid: 4c4e991f-3839-4196-bcfb-eb8464aa55e5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性建構函式的 &#39;ByRef&#39; 參數類型為 &#39;&lt;類型名稱&gt;&#39;；不可以使用具有 byref 參數的建構函式來套用屬性
屬性已使用接受 `ByRef` 參數的屬性建構函式套用至程式設計項目。  
  
 屬性在編譯時期套用，編譯器需要具體值以傳遞至屬性建構函式。`ByRef` 參數接受值的指標，它無法在編譯時期評估。  
  
 您可以定義接受 `ByRef` 參數的屬性建構函式，而且您可以使用它來進行例如繼承的用途，但您套用屬性時，必須使用不接受任何 `ByRef` 參數的建構函式。  
  
 **錯誤 ID︰**BC36006  
  
### 更正這個錯誤  
  
-   請使用不接受任何 `ByRef` 參數的建構函式套用屬性，或完全不套用屬性。  
  
## 請參閱  
 [不在組建中：Visual Basic 屬性概觀](http://msdn.microsoft.com/zh-tw/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Passing Arguments by Value and by Reference](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)   
 [ByRef](../Topic/ByRef%20\(Visual%20Basic\).md)