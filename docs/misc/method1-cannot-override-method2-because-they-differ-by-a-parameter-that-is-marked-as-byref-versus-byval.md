---
title: "&#39;&lt;方法1&gt;&#39; 無法覆寫 &#39;&lt;方法2&gt;&#39;，因為它們的差異只在於參數標記為 &#39;ByRef&#39; 或 &#39;ByVal&#39; 而已 | Microsoft Docs"
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
  - "vbc30398"
  - "bc30398"
helpviewer_keywords: 
  - "BC30398"
ms.assetid: 78d62276-4ad9-4876-8c35-a30c9c195638
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;方法1&gt;&#39; 無法覆寫 &#39;&lt;方法2&gt;&#39;，因為它們的差異只在於參數標記為 &#39;ByRef&#39; 或 &#39;ByVal&#39; 而已
您嘗試使用與已標記 `ByRef` \(非 `ByVal`\) 之參數不同的另一種方法來覆寫方法。 覆寫的成員必須具有與基底類別之繼承成員相同的引數。  
  
 **錯誤 ID︰**BC30398  
  
### 更正這個錯誤  
  
-   請確定參數都是 `ByRef` 或都是 `ByVal`。  
  
## 請參閱  
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Passing Arguments by Value and by Reference](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)