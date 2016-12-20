---
title: "編碼不能設定為 Nothing。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 編碼不能設定為 Nothing。
讀取或寫入檔案的嘗試失敗，因為參數 `encoding` 已設定為 `Nothing`，但需要有效的值。  
  
 <xref:System.Text.Encoding> 用來判斷在寫入檔案時要使用的編碼方式。 預設值為 UTF\-8。  
  
### 更正這個錯誤  
  
-   請為 `encoding` 參數提供有效的值。  
  
## 請參閱  
 [File Encodings](../Topic/File%20Encodings%20\(Visual%20Basic\).md)   
 [Reading from Files](../Topic/Reading%20from%20Files%20in%20Visual%20Basic.md)   
 [Writing to Files](../Topic/Writing%20to%20Files%20in%20Visual%20Basic.md)   
 [My.Computer.FileSystem.ReadAllText 方法](http://msdn.microsoft.com/zh-tw/3a7ac8be-fb1d-4087-bc65-167d6754d57f)   
 [My.Computer.FileSystem.WriteAllText 方法](http://msdn.microsoft.com/zh-tw/f507460c-87d9-4504-b74f-3ff825c7d5c4)