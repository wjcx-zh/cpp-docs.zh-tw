---
title: "無法合併 VbStrConv.Wide 和 VbStrConv.Narrow | Microsoft Docs"
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
  - "vbrArgument_IllegalWideNarrow"
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法合併 VbStrConv.Wide 和 VbStrConv.Narrow
您的應用程式嘗試合併 `VbStrConv` 列舉成員 `Wide` 和 `Narrow`，但它們互斥。  
  
### 更正這個錯誤  
  
1.  請移除 `VbStrConv.Wide` 或 `VbStrConv.Narrow`。  
  
## 請參閱  
 <xref:System.Globalization>   
 [NOTINBUILD VbStrConv 列舉](http://msdn.microsoft.com/zh-tw/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [以 .NET Framework 為基礎的國際應用程式簡介](../Topic/Introduction%20to%20International%20Applications%20Based%20on%20the%20.NET%20Framework.md)