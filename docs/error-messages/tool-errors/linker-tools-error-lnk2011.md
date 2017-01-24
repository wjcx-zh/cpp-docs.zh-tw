---
title: "連結器工具錯誤 LNK2011 | Microsoft Docs"
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
  - "LNK2011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2011"
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK2011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未連結先行編譯物件，映像可能無法執行  
  
 如果您使用先行編譯的標頭檔，LINK 就需要連結所有已先行編譯標頭所建立的目的檔。  如果您的原始程式檔可以用來產生其他原始程式檔使用的先行編譯標頭，您現在必須將所建立的目的檔連同先行編譯標頭包含進來。  
  
 例如，如果您編譯一個稱為 STUB.cpp 的檔案，來建立供其他原始程式檔使用的先行編譯標頭，您必須連結 STUB.obj，否則就會出現這個錯誤。  在下列命令列中，第一行是用來建立由第二、三行的 PROG1.cpp 和 PROG2.cpp 所使用的先行編譯標頭 COMMON.pch。  STUB.cpp 檔案只包含 `#include` 行 \(與 PROG1.cpp 和 PROG2.CPP 的 `#include` 行相同\)，而且僅用來產生先行編譯標頭。  最後一行必須連結 STUB.obj，才可以避免 LNK2011。  
  
```  
cl /c /Yccommon.h stub.cpp  
cl /c /Yucommon.h prog1.cpp  
cl /c /Yucommon.h prog2.cpp  
link /out:prog.exe stub.obj prog1.obj prog2.obj  
```