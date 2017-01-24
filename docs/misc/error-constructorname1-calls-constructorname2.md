---
title: "&lt;錯誤&gt;: &#39;&lt;建構函式名稱1&gt;&#39; 呼叫 &#39;&lt;建構函式名稱2&gt;&#39; | Microsoft Docs"
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
  - "vbc30297"
  - "bc30297"
helpviewer_keywords: 
  - "BC30297"
ms.assetid: dfca67d7-f4d7-4451-a937-68f22b8527d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;錯誤&gt;: &#39;&lt;建構函式名稱1&gt;&#39; 呼叫 &#39;&lt;建構函式名稱2&gt;&#39;
進行循環建構函式呼叫。 建構函式呼叫 `Me.New()` 或 `MyClass.New()`。 其中一個可能的原因是嘗試使用不同的引數清單來呼叫多載建構函式。  
  
 **錯誤 ID︰**BC30297  
  
### 更正這個錯誤  
  
-   使用不同的引數清單來呼叫多載建構函式。  
  
-   如果沒有可存取的多載，請移除 `Me.New()` 或 `MyClass.New()` 呼叫。  
  
## 請參閱  
 [不在組建中：使用建構函式和解構函式](http://msdn.microsoft.com/zh-tw/548eebe1-86c4-4377-b2f5-447cb8be3d90)