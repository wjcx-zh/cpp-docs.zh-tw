---
title: "只在當做執行個體建構函式中的第一個陳述式時，建構函式呼叫才有效。 | Microsoft Docs"
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
  - "vbc30282"
  - "bc30282"
helpviewer_keywords: 
  - "BC30282"
ms.assetid: c51b172f-fbd7-4ef5-8276-01a4bf6ed35b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 只在當做執行個體建構函式中的第一個陳述式時，建構函式呼叫才有效。
`New()` 是在建構函式的第一個陳述式之後呼叫。 如果某個建構函式會明確地呼叫另一個建構函式，則在 `Sub New()` 陳述式後面的第一個陳述式中也必須這麼做。  
  
 **錯誤 ID：**BC30282  
  
### 更正這個錯誤  
  
-   請移除 `New()` 的呼叫，或將它移至建構函式的開頭。  
  
## 請參閱  
 [不在組建中：使用建構函式和解構函式](http://msdn.microsoft.com/zh-tw/548eebe1-86c4-4377-b2f5-447cb8be3d90)