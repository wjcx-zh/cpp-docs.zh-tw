---
title: "Argument is missing in &#39;\&#39; escape sequence. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_RE_ESCAPEMISSINGARG"
  - "vs.message.0x800A00BD"
ms.assetid: 5bd6559b-8cd9-450f-91c8-335ff1b1ef86
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Argument is missing in &#39;\&#39; escape sequence.
在搜尋或取代期間於搜尋字串中使用規則運算式或萬用字元時，通常就會發生這個錯誤。  這個錯誤是模式比對結尾的單一反斜線 \(`\`\) 或輸入沒有十六進位 Unicode 字元的 `\x` 或 `\u` 所造成的。  
  
### 若要更正這個錯誤  
  
1.  要使用規則運算式逸出字元 \(Escape Character\) 進行搜尋，請輸入 `\`。  
  
2.  若要搜尋 Unicode 字元，請輸入 `\x` 或 `\u`，後面接一個有效的 Unicode 值。  
  
3.  要搜尋常值 \(Literal\) 反斜線，請使用 `\\`。  
  
## 請參閱  
 [在 Visual Studio 中使用規則運算式](../Topic/Using%20Regular%20Expressions%20in%20Visual%20Studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/zh-tw/dad03582-4931-4893-83ba-84b37f5b1600)   
 [檔案中尋找](../Topic/Find%20in%20Files.md)