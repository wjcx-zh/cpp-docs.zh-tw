---
title: "&#39;&lt;方法1&gt;&#39; 無法覆寫 &#39;&lt;方法2&gt;&#39;，因為其選擇性參數的預設值不同 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30307"
  - "bc30307"
helpviewer_keywords: 
  - "BC30307"
ms.assetid: c4cf6040-41c3-4650-8eb9-bff063756599
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;方法1&gt;&#39; 無法覆寫 &#39;&lt;方法2&gt;&#39;，因為其選擇性參數的預設值不同
您嘗試以另一個方法覆寫某個方法，但其選擇性參數的預設值與後者不同，這表示兩者的簽章不同。 類型可能會藉由宣告具有相同名稱和特徵標記的方法，並使用 `Overrides` 修飾詞標記宣告，來覆寫繼承的可覆寫方法。  
  
 **錯誤 ID︰**BC30307  
  
### 更正這個錯誤  
  
-   確定兩個方法具有相同的特徵標記。  
  
## 請參閱  
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [不在組建中：覆寫修飾詞](http://msdn.microsoft.com/zh-tw/18e8ef02-e79b-470e-837a-46a8f4163d32)