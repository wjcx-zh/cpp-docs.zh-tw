---
title: "&#39;&lt;方法1&gt;&#39; 無法覆寫 &#39;&lt;方法2&gt;&#39;，因為它是 &#39;Declare&#39; 陳述式 | Microsoft Docs"
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
  - "vbc30474"
  - "bc30474"
helpviewer_keywords: 
  - "BC30474"
ms.assetid: 7277e8cc-aa3c-40c3-8682-c8c42d2ee921
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;方法1&gt;&#39; 無法覆寫 &#39;&lt;方法2&gt;&#39;，因為它是 &#39;Declare&#39; 陳述式
您嘗試要覆寫基底類別名稱以 `Declare` 陳述式宣告的委派。  
  
 **錯誤識別碼：**BC30474  
  
### 更正這個錯誤  
  
1.  變更已覆寫的成員，讓它不是 `Declare` 陳述式。  
  
2.  請勿嘗試覆寫這個方法。  
  
## 請參閱  
 [Declare Statement](../Topic/Declare%20Statement.md)   
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)