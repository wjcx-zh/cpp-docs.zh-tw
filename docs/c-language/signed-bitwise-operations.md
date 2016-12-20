---
title: "帶正負號的位元運算 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "位元運算"
  - "帶正負號的位元運算"
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 帶正負號的位元運算
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.3**：帶正負號整數位元運算的結果  
  
 帶正負號整數的位元運算運作方式，與不帶正負號整數的位元運算相同。  例如，`–16 & 99` 可以用二進位運算式表示為  
  
```  
  11111111 11110000  
& 00000000 01100011  
  _________________  
  00000000 01100000  
```  
  
 位元 AND 的結果為 96。  
  
## 請參閱  
 [整數](../c-language/integers.md)