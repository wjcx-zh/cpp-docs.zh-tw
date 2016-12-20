---
title: "編譯器錯誤 C2773 | Microsoft Docs"
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
  - "C2773"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2773"
ms.assetid: 8d564b26-1623-4d92-aabc-dff33f7b1145
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2773
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#import 和 \#using 只可以在 C\+\+ 編譯器中使用  
  
 C 編譯器無法辨識 `#import` 前置處理器指示詞 \(Preprocessor Directive\)。  請將來源檔編譯成 C\+\+。  必要時，請使用 [\/TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)。