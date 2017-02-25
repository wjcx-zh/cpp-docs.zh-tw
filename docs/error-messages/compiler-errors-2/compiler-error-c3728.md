---
title: "編譯器錯誤 C3728 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3728"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3728"
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C3728
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'event' : 事件沒有引發方法  
  
 以 C\# 之類語言建立而不允許事件自本身所定義之類別以外引發的中繼資料，是透過 [\#using](../../preprocessor/hash-using-directive-cpp.md) 指示詞加以包含，而使用 CLR 程式設計的 Visual C\+\+ 程式則試圖引發該事件。  
  
 若要在以 C\# 之類的語言開發的程式中引發事件，包含該事件的類別必須同時定義引發該事件的公用方法。