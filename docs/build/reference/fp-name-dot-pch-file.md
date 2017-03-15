---
title: "/Fp (命名 .Pch 檔案) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.PrecompiledHeaderFile"
  - "/fp"
  - "VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 檔案, 命名"
  - "/Fp 編譯器選項 [C++]"
  - "Fp 編譯器選項 [C++]"
  - "-Fp 編譯器選項 [C++]"
  - "名稱 [C++], PCH"
  - "命名先行編譯器標頭檔"
  - "PCH 檔案, 命名"
  - "先行編譯標頭檔, 命名"
ms.assetid: 0fcd9cbd-e09f-44d3-9715-b41efb5d0be2
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Fp (命名 .Pch 檔案)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供先行編譯標頭的路徑名稱，而不要使用預設路徑名稱。  
  
## 語法  
  
```  
/Fppathname  
```  
  
## 備註  
 使用這個選項配合 [\/Yc \(建立先行編譯標頭檔\)](../../build/reference/yc-create-precompiled-header-file.md) 或 [\/Yu \(使用先行編譯標頭檔\)](../../build/reference/yu-use-precompiled-header-file.md)，以提供先行編譯標頭的路徑名稱，而不使用預設的路徑名稱。  您也可以使用 **\/Fp** 配合 **\/Yc**，指定使用與 **\/Yc** `filename` 引數不同，也與原始程式檔主檔名不同的先行編譯標頭檔 \(Precompiled Header File\)。  
  
 如果您不指定副檔名做為路徑名稱的一部分，就會假設副檔名為 .pch。  如果您指定目錄而沒有檔名，預設的檔名為 VC`x`0.pch.，其中 `x` 為所使用 Visual C\+\+ 的主要版本。  
  
 您也可以使用 **\/Fp** 選項搭配 **\/Yu**。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**先行編譯標頭**\] 屬性頁。  
  
4.  修改 \[**先行編譯標頭檔**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderFile%2A>。  
  
## 範例  
 如果您想要建立您程式的偵錯版本先行編譯標頭檔，而且要同時編譯標頭檔和原始程式碼兩者，可以指定以下的命令：  
  
```  
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP  
```  
  
## 範例  
 以下命令是指定使用名為 MYPCH.pch 的先行編譯標頭檔。  編譯器會假設 PROG.cpp 中的原始程式碼已經透過 MYAPP.h 先行編譯過，而且先行編譯的程式碼是位於 MYPCH.pch 中。  它會使用 MYPCH.pch 的內容並且編譯 PROG.cpp 的其餘部分來建立 .obj 檔案。  這個範例的輸出是一個名為 PROG.exe 的檔案。  
  
```  
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP  
```  
  
## 請參閱  
 [輸出檔 \(\/F\) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [指定路徑名稱](../../build/reference/specifying-the-pathname.md)