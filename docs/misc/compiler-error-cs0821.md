---
title: "編譯器錯誤 CS0821 | Microsoft Docs"
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
  - "CS0821"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0821"
ms.assetid: ef449115-93e8-4fa5-848a-d30dc7f68ddf
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0821
隱含類型區域變數不可為 fixed  
  
 在 `fixed` 內容中不支援隱含類型區域變數和匿名類型。  
  
### 更正這個錯誤  
  
1.  請從變數移除 `fixed` 修飾詞，或為變數指定明確類型。  
  
## 範例  
 下列程式碼會產生 CS0821：  
  
```  
class A { static int x; public static int Main() { unsafe { fixed (var p = &x) { } } return -1; } }  
```  
  
## 請參閱  
 [隱含類型區域變數](../Topic/Implicitly%20Typed%20Local%20Variables%20\(C%23%20Programming%20Guide\).md)