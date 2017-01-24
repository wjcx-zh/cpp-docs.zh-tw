---
title: "使用類型 &#39;Object&#39; 的引數時，請以 &#39;FilePutObject&#39; 代替 &#39;FilePut&#39; | Microsoft Docs"
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
  - "vbrUseFilePutObject"
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 使用類型 &#39;Object&#39; 的引數時，請以 &#39;FilePutObject&#39; 代替 &#39;FilePut&#39;
`FilePut` 方法包含類型`Object` 的引數。`FilePutObject` 應該用於取代 `FilePut`，以避免模稜兩可。  
  
### 更正這個錯誤  
  
-   將 `FilePut` 取代為 `FilePutObject`。  
  
-   請將 `Object` 引數轉換為更特定的類型。  
  
-   使用 `My.Computer.FileSystem` 物件中可用的功能。  
  
## 請參閱  
 [不在組建中：FilePutObject 函式](http://msdn.microsoft.com/zh-tw/a0f52a1c-5ecc-4945-b18c-03147af61d6b)   
 [My.Computer.FileSystem Object](../Topic/My.Computer.FileSystem%20Object.md)   
 [My.Computer.FileSystem.WriteAllBytes 方法](http://msdn.microsoft.com/zh-tw/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)