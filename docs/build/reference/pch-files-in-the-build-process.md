---
title: "建置程序中的 PCH 檔 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 檔案, 建置程序"
  - "Makefile, 建置程序中的 PCH 檔"
  - "PCH 檔案, 建置程序"
ms.assetid: ebb4b368-8a11-4009-b347-01e79af02fbc
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建置程序中的 PCH 檔
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

軟體專案的程式碼基底通常包含於多個 C 或 C\+\+ 原始程式檔、目的檔、程式庫和標頭檔中。  通常，Makefile 會將這些項目的組合組織成一個可執行檔。  下圖顯示使用先行編譯標頭檔之 Makefile 的結構。  此圖表中的 NMAKE 巨集名稱和檔名與 [PCH 的 Makefile 範例](../../build/reference/sample-makefile-for-pch.md)和 [PCH 的範例程式碼](../../build/reference/example-code-for-pch.md)中的範例程式碼一致。  
  
 此圖使用三種圖形來顯示建置程序的流程。  標有名稱的矩形代表各個檔案或巨集；三個巨集代表一個或多個檔案。  灰色區域代表各個編譯或連結動作。  箭頭顯示在編譯或連結程序內結合的檔案和巨集。  
  
 ![使用先行編譯標頭檔的 Makefile](../../build/reference/media/vc30ow1.png "vc30OW1")  
使用先行編譯標頭檔之 Makefile 的結構  
  
 在本圖的最上方開始，STABLEHDRS 和 BOUNDRY 都是 NMAKE 巨集，您可在其中列出並不需要重新編譯的檔案。  只有在先行編譯標頭檔 \(STABLE.pch\) 不存在，或是您變更兩個巨集中所列示的檔案時，才使用命令字串  
  
```  
CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp  
```  
  
 編譯這些檔案。  不論是哪一種情況，先行編譯標頭檔只會包含 STABLEHDRS 巨集中所列示的檔案內的程式碼。  請在 BOUNDRY 巨集中列出您想先行編譯的最後一個檔案。  
  
 您在這些巨集中列出的檔案可以是標頭檔或 C 或 C\+\+ 原始程式檔 \(單一 .pch 檔不可同時與 C 和 C\+\+ 模組一起使用\)。請注意，您可在 BOUNDRY 檔案內的某一點上使用 **hdrstop** 巨集來停止先行編譯。  如需詳細資訊，請參閱 [hdrstop](../../preprocessor/hdrstop.md)。  
  
 從圖表繼續往下看，APPLIB.obj 代表您最終應用程式中使用的支援程式碼。  它是以 UNSTABLEHDRS 巨集中列示的檔案 APPLIB.cpp 及先行編譯標頭中的先行編譯程式碼建立而成。  
  
 MYAPP.obj 表示您最終的應用程式。  它是以 UNSTABLEHDRS 巨集中列示的檔案 MYAPP.cpp 及先行編譯標頭中的先行編譯程式碼建立而成。  
  
 最後，連結 OBJS 巨集中列示的檔案 \(APPLIB.obj 和 MYAPP.obj\) 建立可執行檔 \(MYAPP.EXE\)。  
  
 如需此圖的進一步說明，請參閱：  
  
-   [PCH 的 Makefile 範例](../../build/reference/sample-makefile-for-pch.md)  
  
-   [PCH 範例程式碼](../../build/reference/example-code-for-pch.md)  
  
## 請參閱  
 [在專案中使用先行編譯的標頭](../../build/reference/using-precompiled-headers-in-a-project.md)