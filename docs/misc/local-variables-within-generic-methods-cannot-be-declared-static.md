---
title: "泛型方法內的區域變數不可以宣告為 &#39;Static&#39; | Microsoft Docs"
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
  - "vbc32068"
  - "bc32068"
helpviewer_keywords: 
  - "BC32068"
ms.assetid: cb5df484-76f9-4092-9d19-f26ddcf1c035
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 泛型方法內的區域變數不可以宣告為 &#39;Static&#39;
泛型程序內的區域變數宣告會指定 `Static`。  
  
 Visual Basic 和 .NET Framework 目前不支援任何的靜態變數和泛型程序組合。  
  
 **錯誤 ID︰**BC32068  
  
### 更正這個錯誤  
  
-   請從變數宣告中移除 `Static` 關鍵字。  
  
## 請參閱  
 [Static](../Topic/Static%20\(Visual%20Basic\).md)   
 [NOTINBUILD 如何：延長變數的存留期](http://msdn.microsoft.com/zh-tw/04e7c56c-1db0-4fe5-a678-859a39ec654b)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)