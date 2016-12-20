---
title: "全形字元不可以當做 XML 分隔符號 | Microsoft Docs"
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
  - "vbc31197"
  - "bc31197"
helpviewer_keywords: 
  - "BC31197"
ms.assetid: f5d724f8-545b-4cf8-9606-12c63814c6e8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 全形字元不可以當做 XML 分隔符號
XML 常值已定義，其中包含作為分隔符號的全形字元。 全形字元也稱為寬字元或多位元組字元。  
  
 **錯誤 ID︰**BC31197  
  
### 更正這個錯誤  
  
-   從 XML 常值定義中移除全形字元，並取代為有效的 ANSI 分隔符號字元。 有效的分隔符號字元包括：`<`、`>`、`=`、`:`、`/`。  
  
## 請參閱  
 [XML Literals](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [.NET Framework 中的字元編碼方式](../Topic/Character%20Encoding%20in%20the%20.NET%20Framework.md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)