---
title: "&#39;&lt;方法1&gt;&#39; 無法覆寫 &#39;&lt;方法2&gt;&#39;，因為它們的傳回類型不同 | Microsoft Docs"
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
  - "bc30437"
  - "vbc30437"
helpviewer_keywords: 
  - "BC30437"
ms.assetid: e566ae72-c597-4b33-b70d-5d4ea879d644
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;方法1&gt;&#39; 無法覆寫 &#39;&lt;方法2&gt;&#39;，因為它們的傳回類型不同
您嘗試使用傳回類型不同的另一個方法來覆寫方法。 類型可能會藉由宣告具有相同名稱和特徵標記的方法，並使用 `Overrides` 修飾詞標記宣告，來覆寫繼承的可覆寫方法。 兩個方法的簽章必須相符。  
  
 **錯誤 ID︰**BC30437  
  
### 更正這個錯誤  
  
-   請檢查兩個方法的傳回類型，並視需要將它們變更為相符。  
  
## 請參閱  
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)