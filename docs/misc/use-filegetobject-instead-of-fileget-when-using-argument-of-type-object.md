---
title: "使用類型 &#39;Object&#39; 的引數時，請以 &#39;FileGetObject&#39; 代替 &#39;FileGet&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 使用類型 &#39;Object&#39; 的引數時，請以 &#39;FileGetObject&#39; 代替 &#39;FileGet&#39;
`FileGet` 方法包含類型 `Object` 的引數。`FileGetObject` 應該用於取代 `FileGet`，以避免模稜兩可。  
  
 請注意，`My.Computer.Filesystem` 所提供的功能比 `FileGet` 或 `FileGetObject` 更容易使用和執行。  
  
### 更正這個錯誤  
  
1.  將 `FileGet` 取代為 `FileGetObject`。  
  
2.  請將 `Object` 引數轉換為更特定的類型。  
  
## 請參閱  
 [不在組建中：FileGetObject 函式](http://msdn.microsoft.com/zh-tw/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)   
 [My.Computer.FileSystem Object](../Topic/My.Computer.FileSystem%20Object.md)