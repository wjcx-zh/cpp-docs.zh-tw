---
title: "Friend 組件參考 &lt;參考&gt; 無效。 InternalsVisibleTo 宣告不能指定版本、文化特性、公開金鑰語彙基元或處理器架構。 | Microsoft Docs"
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
  - "bc31534"
  - "vbc31534"
helpviewer_keywords: 
  - "BC31534"
ms.assetid: ae1e470e-3105-48f2-87b1-466e395a7d44
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Friend 組件參考 &lt;參考&gt; 無效。 InternalsVisibleTo 宣告不能指定版本、文化特性、公開金鑰語彙基元或處理器架構。
傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性建構函式的組件名稱包含 `Version`、`Culture`、`PublicKeyToken` 或 `processorArchitecture` 屬性。  
  
 **錯誤 ID：**BC31534  
  
### 更正這個錯誤  
  
1.  從傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性建構函式的組件名稱中移除 `Version`、`Culture`、`PublicKeyToken` 或 `processorArchitecture` 屬性。  
  
## 請參閱  
 <xref:System.Reflection.AssemblyName>   
 [不在組建中：Friend 組件 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/80e7a33a-ca91-450b-a00e-c5a7986e228c)