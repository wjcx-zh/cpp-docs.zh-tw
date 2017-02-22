---
title: "/Yc (建立先行編譯標頭檔) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.UsePrecompiledHeader"
  - "/yc"
  - "VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough"
  - "VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader"
  - "VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 檔案, 建立"
  - "/Yc 編譯器選項 [C++]"
  - "PCH 檔案, 建立"
  - "先行編譯標頭檔, 建立"
  - "Yc 編譯器選項 [C++]"
  - "-Yc 編譯器選項 [C++]"
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /Yc (建立先行編譯標頭檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指示編譯器建立代表某特定點之編譯狀態的先行編譯標頭檔 \(.pch\)。  
  
## 語法  
  
```  
/Yc[filename]  
```  
  
## Arguments  
 `filename`  
 指定標頭 \(.h\) 檔。  使用這個引數時，編譯器會編譯一直到 .h 檔 \(也包含該檔\) 的所有程式碼。  
  
## 備註  
 指定 **\/Yc** 而不加引數時，編譯器會編譯所有程式碼一直到主原始程式檔結尾，或者到主檔案中發生 [hdrstop](../../preprocessor/hdrstop.md) 的點。  除非您使用  **hdrstop** Pragma 或 **\/Fp** 選項指定了不同的檔名，否則所產生的 .pch 檔會具有與主原始程式檔相同的主檔名。  
  
 先行編譯的程式碼會儲存在以 **\/Yc** 選項指定之檔案的主檔名和 .pch 副檔名所組成名稱的檔案中。  您也可以使用 [\/Fp \(命名 .Pch 檔案\)](../../build/reference/fp-name-dot-pch-file.md) 選項，指定先行編譯標頭檔的名稱。  
  
 如果您使用 **\/Yc**`filename`，編譯器會編譯所有程式碼一直到指定供後續使用 **\/Yu** 選項的檔案 \(也包含該檔\)。  
  
 如果 **\/Yc**`filename` 和 [\/Yu \(使用先行編譯標頭檔\)](../../build/reference/yu-use-precompiled-header-file.md)`filename` 選項出現在相同的命令列中，而且兩者都參考 \(或隱含\) 相同的檔案名稱，**\/Yc**`filename` 會取得優先權。  這項功能簡化了 Makefile 的撰寫。  
  
 如需先行編譯標頭的詳細資訊，請參閱：  
  
-   [\/Y \(先行編譯標頭\)](../../build/reference/y-precompiled-headers.md)  
  
-   [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  選取 .cpp 檔。  .cpp 檔必須 \#include 其中包含先行編譯標頭檔資訊的 .h 檔。  專案的 **\/Yc** 設定可以在檔案層級加以覆寫。  
  
2.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
3.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
4.  按一下 \[**先行編譯標頭**\] 屬性頁。  
  
5.  修改 \[**透過檔案建立\/使用 PCH**\] 屬性或 \[**建立\/使用先行編譯標頭檔**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A>以及<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>。  
  
## 範例  
 請考慮下列程式碼：  
  
```  
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
...  
```  
  
 此程式碼是以 `CL /YcMYAPP.H PROG.CPP` 命令編譯，編譯器會將 AFXWIN.h、RESOURCE.h 和 MYAPP.h 的所有前置處理儲存在名為 MYAPP.pch 的先行編譯標頭檔中。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)