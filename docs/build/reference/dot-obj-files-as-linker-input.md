---
title: ".Obj 檔做為連結器輸入 | Microsoft Docs"
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
helpviewer_keywords: 
  - ".obj 檔做為連結器輸入"
  - "COFF 檔案"
  - "LINK 工具 [C++], .obj 檔案"
  - "連結器 [C++], OBJ 檔做為輸入"
  - "OBJ 檔做為連結器輸入"
  - "目的檔, 連結器輸出"
  - "OMF 目的檔"
ms.assetid: 3028e423-8b10-4972-8eb4-6e9ae58f0a26
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .Obj 檔做為連結器輸入
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

連結器工具 \(LINK.EXE\) 可以接受通用物件檔案格式 \(COFF\) 的 .obj 檔案。  
  
## 備註  
 Microsoft 提供您一份用於定義通用物件檔案格式的可下載文件。  如需詳細資訊，請下載[Microsoft 可攜式執行檔和通用物件檔案格式規格](http://go.microsoft.com/fwlink/?LinkId=93292)\(英文\) 修訂本 8.1 \(含\) 以後。  
  
## Unicode 支援  
 從 Visual Studio 2005 開始，Microsoft Visual C\+\+ 編譯器支援識別項中的 Unicode 字元，其定義如同 ISO\/IEC C 和 C\+\+ 標準一樣。  舊版的編譯器僅支援識別項中的 ASCII 字元。  為了支援函式、類別和靜態方法名稱中的 Unicode，編譯器和連結器會對 .obj 檔案中的 COFF 符號使用 Unicode UTF\-8 編碼方式。  UTF\-8 編碼方式可以與舊版 Visual Studio 所使用的 ASCII 編碼方式，進行向上相容。  
  
 如需編譯器和連結器的詳細資訊，請參閱[編譯器和連結器中的 Unicode 支援](../../build/reference/unicode-support-in-the-compiler-and-linker.md)。  如需 Unicode 標準的詳細資訊，請參閱組織 [Unicode](http://go.microsoft.com/fwlink/?LinkId=37123) 。  
  
## 請參閱  
 [LINK 輸入檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [Unicode 的支援](../../text/support-for-unicode.md)   
 [編譯器和連結器中的 Unicode 支援](../../build/reference/unicode-support-in-the-compiler-and-linker.md)   
 [Unicode 標準](http://go.microsoft.com/fwlink/?LinkId=37123)   
 [通用物件檔案格式規格。](http://go.microsoft.com/fwlink/?LinkId=93292)