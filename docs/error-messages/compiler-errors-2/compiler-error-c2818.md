---
title: "編譯器錯誤 C2818 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2818"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2818"
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2818
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

多載 'operator \-\>' 的應用程式透過型別 'type' 遞迴  
  
 類別成員存取運算子 \(Member Access Operator\) 的重新定義包含遞迴的 `return` 陳述式 \(Statement\)。  若要將 `->` 運算子重新定義為具有遞迴，必須將遞迴常式移至可從運算子覆寫函式呼叫的另一個函式中。