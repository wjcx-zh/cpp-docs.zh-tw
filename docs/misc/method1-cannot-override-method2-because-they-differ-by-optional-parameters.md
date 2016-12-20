---
title: "&#39;&lt;方法1&gt;&#39; 不能覆寫 &#39;&lt;方法2&gt;&#39;，因為其選擇性參數不同。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30308"
  - "bc30308"
helpviewer_keywords: 
  - "BC30308"
ms.assetid: 591dc351-4b87-4e92-81e1-2c1ff51da295
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;方法1&gt;&#39; 不能覆寫 &#39;&lt;方法2&gt;&#39;，因為其選擇性參數不同。
您嘗試以另一個方法覆寫某個方法，但其選擇性參數的值與後者不同，這表示兩者的特徵標記不同。 類型可能會藉由宣告具有相同名稱和特徵標記的方法，並使用 `Overrides` 修飾詞標記宣告，來覆寫繼承的可覆寫方法。  
  
 **錯誤識別碼：**BC30308  
  
### 更正這個錯誤  
  
-   確定兩個方法具有相同的特徵標記。  
  
## 請參閱  
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)