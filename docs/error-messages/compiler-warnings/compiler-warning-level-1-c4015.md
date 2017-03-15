---
title: "編譯器警告 (層級 1) C4015 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4015"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4015"
ms.assetid: 7242ab90-c869-482f-8152-46728575837e
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4015
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 位元欄位的型別必須為整數  
  
 位元欄位 \(Bit Field\) 未宣告為整數型別 \(Integer Type\)。  編譯器假設位元欄位的基底型別 \(Base Type\) 為不帶正負號的。  位元欄位必須宣告為不帶正負號的整數 \(Unsigned Integer\) 型別。