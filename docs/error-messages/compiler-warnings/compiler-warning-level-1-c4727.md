---
title: "編譯器警告 (層級 1) C4727 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4727"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4727"
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 編譯器警告 (層級 1) C4727
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"有相同時間戳記的 PCH 具名 pch\_file 出現在 obj\_file\_1 和 obj\_file\_2 中，使用第一個 PCH。  
  
 以 **\/Yc** 編譯多個編譯時，此時編譯器可以用相同的 .pch 時間戳記標示所有的 .obj 檔，就會發生 C4727。  
  
 若要解決這個問題，請以 **\/Yc \/c** 編譯一個原始程式檔 \(建立 pch\)，而另外以 **\/Yu \/c** 進行其他編譯 \(使用 pch\)，然後將所有編譯連結在一起。  
  
 因此，如果執行下列動作，就會產生 C4727：  
  
 **cl \/clr \/GL a.cpp b.cpp c.cpp \/Ycstdafx.h**  
  
 您可以改執行以下動作：  
  
 **cl \/clr \/GL a.cpp \/Ycstdafx.h \/c**  
  
 **cl \/clr \/GL b.cpp c.cpp \/Yustdafx.h \/link a.obj**  
  
 如需詳細資訊，請參閱  
  
-   [\/Yc \(建立先行編譯標頭檔\)](../../build/reference/yc-create-precompiled-header-file.md)  
  
-   [\/Yu \(使用先行編譯標頭檔\)](../../build/reference/yu-use-precompiled-header-file.md)