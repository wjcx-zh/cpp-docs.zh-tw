---
title: "/Z7、/Zi、/ZI (偵錯資訊格式) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.DebugInformationFormat"
  - "/zi"
  - "/z7"
  - "VC.Project.VCCLWCECompilerTool.DebugInformationFormat"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C7 相容編譯器選項 [C++]"
  - "-Zl 編譯器選項 [C++]"
  - "偵錯資訊格式編譯器選項"
  - "ZI 編譯器選項"
  - "-Zi 編譯器選項 [C++]"
  - "/ZI 編譯器選項 [C++]"
  - "Z7 編譯器選項 [C++]"
  - "偵錯 [C++]，偵錯資訊檔案"
  - "Zi 編譯器選項 [C++]"
  - "none 編譯器選項 [C++]"
  - "/Zi 編譯器選項 [C++]"
  - "程式資料庫編譯器選項 [C++]"
  - "完整符號偵錯資訊"
  - "/Z7 編譯器選項 [C++]"
  - "僅限行號編譯器選項 [C++]"
  - "cl.exe 編譯器，偵錯選項"
  - "-Z7 編譯器選項 [C++]"
ms.assetid: ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# /Z7、/Zi、/ZI (偵錯資訊格式)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

選取為程式所建立的偵錯資訊類型，以及此資訊是保留在物件檔 \(.obj\) 還是在程式資料庫 \(PDB\)。  
  
## 語法  
  
```  
/Z{7|i|I}  
```  
  
## 備註  
 請參閱下表描述的選項。  
  
 無  
 不產生偵錯資訊，讓編譯快一些。  
  
 **\/Z7**  
 產生 .obj 檔案，其中包含供偵錯工具使用的完整符號偵錯資訊。  符號偵錯資訊包含了變數的名稱和類型，以及函式與行號。  不會產生 .pdb 檔案。  
  
 沒有 .pdb 檔，對散發程式庫的協力廠商來說有好處。  不過，在連結階段和偵錯期間就必須要有先行編譯標頭的 .obj 檔。  如果 .pch 目的檔中只有類型資訊 \(而沒有程式碼\)，您也必須以 [\/Yl \(插入偵錯程式庫的 PCH 參考\)](../../build/reference/yl-inject-pch-reference-for-debug-library.md) 來編譯。  
  
 **\/Zi**  
 產生程式資料庫 \(PDB\)，內含與偵錯工具一起使用的類型資訊和符號偵錯資訊。  符號偵錯資訊包含了變數的名稱和類型，以及函式與行號。  
  
 **\/Zi** 不會影響最佳化。  不過，**\/Zi** 確實隱含 **\/debug**。如需詳細資訊，請參閱 [\/DEBUG \(產生偵錯資訊\)](../../build/reference/debug-generate-debug-info.md)。  
  
 類型資訊是放置於 .pdb 檔中，而不是 .obj 檔中。  
  
 您可以使用 [\/Gm \(啟用最少重建\)](../../build/reference/gm-enable-minimal-rebuild.md) 搭配 **\/Zi**，然而以 **\/Z7** 編譯時，就無法使用 **\/Gm**。  
  
 以 **\/Zi** 和 **\/clr** 編譯時，不會將 <xref:System.Diagnostics.DebuggableAttribute> 屬性置於組件中繼資料。如果您需要這個屬性，就必須在原始程式碼中指定。  這個屬性可能影響應用程式的執行階段效能。  如需 Debuggable 屬性如何影響效能，以及如何減輕效能影響的詳細資訊，請參閱[使映像偵錯更容易](../Topic/Making%20an%20Image%20Easier%20to%20Debug.md)。  
  
 **\/ZI**  
 產生其格式可支援 \[編輯後繼續\] 功能的程式資料庫 \(如上所述\)。  如果您希望使用「編輯後繼續」偵錯，就必須使用這個選項。  由於大部分最佳化都與「編輯後繼續」不相容，請使用 **\/ZI** 停用程式碼中任何 `#pragma optimize` 陳述式。  
  
 **\/ZI** 會導致您在編譯中使用 [\/Gy \(啟用函式階層連結\)](../../build/reference/gy-enable-function-level-linking.md) 和 [\/FC \(診斷中的原始程式碼檔之完整路徑\)](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)。  
  
 **\/ZI** 與 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md) 不相容。  
  
> [!NOTE]
>  **\/ZI** 僅供以 x86 為目標的編譯器使用，這個編譯器選項不提供以 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 或 ARM 處理器為目標的編譯器使用。  
  
 編譯器會將程式資料庫命名為 *project*.pdb。  如果編譯不含專案的檔案，編譯器會建立名為 VC*x*0.pdb 的資料庫，其中 *x* 是使用中 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 的主要版本。  編譯器會將 PDB 的名稱嵌入每一個使用這個選項建立的 .obj 檔案，並將偵錯工具指向符號和行號資訊的位置。  使用這個選項時，您的 .obj 檔案會變得小一些，因為偵錯資訊是儲存在 .pdb 檔案中，而不是儲存在 .obj 檔案中。  
  
 如果您從使用這個選項編譯的物件建立程式庫，則關聯的 .pdb 檔案必須在程式庫連結至程式時可供使用。  因此，如果您要散發程式庫，就必須同時散發 PDB。  
  
 若要建立含有偵錯資訊的程式庫而不使用 .pdb 檔案，您必須選取編譯器的 C 7.0 相容 \(**\/Z7**\) 選項。  如果您使用先行編譯標頭選項，先行編譯標頭與原始程式碼其餘部分的偵錯資訊都會置入 PDB 中。  指定 \[程式資料庫\] 選項時，會忽略 **\/Yd** 選項。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**一般**\] 屬性頁。  
  
4.  修改 \[**偵錯資訊格式**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)