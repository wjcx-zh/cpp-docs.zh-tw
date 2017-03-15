---
title: "編譯器和連結器中的 Unicode 支援 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.UseUnicodeResponseFiles"
  - "VC.Project.VCLibrarianTool.UseUnicodeResponseFiles"
  - "VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles"
  - "VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unicode, Visual C++"
ms.assetid: acc1d322-56b9-4696-a30e-2af891a4e288
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器和連結器中的 Unicode 支援
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題描述 Visual C\+\+ 建置工具中的 Unicode 支援。  
  
 檔名  
 命令列上指定的檔案名稱或編譯器指示詞 \(例如 \#include\) 現在可以包含 Unicode 字元。  
  
 原始程式檔  
 Unicode 字元現在在識別項、巨集、字串和字元常值 \(Character Literal\)，以及註解中都支援。通用字元名稱現在也支援。  
  
 Unicode 可以下列編碼方式輸入原始程式檔中：  
  
-   UTF\-16 位元組由小到大，加或不加位元組順序標記 \(BOM\)  
  
-   UTF\-16 位元組由大到小，加或不加 BOM  
  
-   UTF\-8 加 BOM  
  
 Output  
 在編譯期間，編譯器會以 UTF\-16 輸出診斷至主控台 \(Console\)。可顯示於主控台的字元，依主控台視窗屬性而定。編譯器輸出重新導向至檔案是以目前的 ANSI 主控台字碼頁執行。  
  
 連結器回應檔和 .DEF 檔案  
 回應檔和 DEF 檔案可以是 UTF\-16 加位元組順序標記或 ANSI。舊版只支援 ANSI。  
  
 .asm 和 .cod dumps  
 .asm 和 .cod dumps 是預設為使用 ANSI，以便與 MASM 相容。使用 \/FAu 輸出 UTF\-8。請注意，如果您指定 \/FAs，混合的原始程式碼會直接列印而可能看起來像亂碼，例如，如果原始程式碼是用 UTF\-8，而您並未指定 \/FAsu 時。  
  
 您可以在開發環境中啟用 Unicode 檔案名稱 \(請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)\)，方法是：選取適當的工具，並選取 \[**啟用 Unicode 回應檔**\] 屬性，這項屬性是預設為啟用。  您要變更這項預設值的其中一個理由是：如果修改開發環境，以便使用沒有 Unicode 支援的編譯器時。  
  
## 請參閱  
 [在命令列中建置](../../build/building-on-the-command-line.md)