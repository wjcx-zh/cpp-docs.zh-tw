---
title: "&#39;&lt;關鍵字&gt;&#39; 在模組中無效 | Microsoft Docs"
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
  - "vbc32001"
  - "bc32001"
helpviewer_keywords: 
  - "BC32001"
ms.assetid: b00757ac-5652-460d-9d2c-11b264d7ec7f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;關鍵字&gt;&#39; 在模組中無效
與類別執行個體相關的關鍵字，例如 `Me` 或 `MyBase`，用在模組內。 模組沒有繼承或執行個體。  
  
 **錯誤 ID：**BC32001  
  
### 更正這個錯誤  
  
-   如果使用關鍵字的程式碼牽涉到類別執行個體，請將它移至類別實作。  
  
-   如果使用關鍵字的程式碼適合模組，請移除無效的關鍵字。  
  
## 請參閱  
 [我](http://msdn.microsoft.com/zh-tw/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyBase \- delete](http://msdn.microsoft.com/zh-tw/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)