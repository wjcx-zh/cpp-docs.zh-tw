---
title: "方法若不在堆疊最上方，將無法設定其區域變數值 | Microsoft Docs"
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
  - "bc30711"
  - "vbc30711"
helpviewer_keywords: 
  - "BC30711"
ms.assetid: b2aa290f-3311-448a-af46-ff2a2add5788
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法若不在堆疊最上方，將無法設定其區域變數值
您只能修改呼叫堆疊最上方的變數。 例如，如果 `procedure1` 呼叫 `procedure2`，而您在 `procedure1` 中，則無法修改 `procedure2` 中的變數。  
  
 **錯誤 ID︰**BC30711  
  
### 更正這個錯誤  
  
-   修改呼叫堆疊最上方的變數。  
  
## 請參閱  
 [Visual Studio 偵錯](../Topic/Debugging%20in%20Visual%20Studio.md)