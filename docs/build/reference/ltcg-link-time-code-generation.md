---
title: "/LTCG (連結時間產生程式碼) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.LinkTimeCodeGeneration"
  - "VC.Project.VCConfiguration.WholeProgramOptimization"
  - "VC.Project.VCCLWCECompilerTool.WholeProgramOptimization"
  - "/ltcg"
  - "VC.Project.VCCLCompilerTool.WholeProgramOptimization"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LTCG 連結器選項"
  - "C++ 連結器中的連結階段程式碼產生"
  - "LTCG 連結器選項"
  - "-LTCG 連結器選項"
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# /LTCG (連結時間產生程式碼)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LTCG[:INCREMENTAL|:NOSTATUS|:STATUS|:OFF|:PGINSTRUMENT|:PGOPTIMIZE|:PGUPDATE]  
```  
  
## 備註  
 :INCREMENTAL \(選擇性\)  
 指定的連結器僅將整個程式最佳化或連結時產生程式碼 \(LTCG\) 套用到受編輯影響的檔案集，而不是套用到整個專案。當指定 \/LTCG 時，預設不會設定此旗標，而且整個專案會使用整個程式最佳化加以連結。  
  
 :NOSTATUS &#124;:STATUS \(選擇性\)  
 指定連結器是否顯示進度指示器，以顯示連結完成的比率。預設不會顯示此狀態資訊。  
  
 :OFF \(選擇性\)  
 停用連結時產生程式碼。此行為與未命令列上指定 \/LTCG 相同。  
  
 :PGINSTRUMENT \(選擇性\)  
 此選項已被取代。若要產生經過檢的組建，以進行特性指引最佳化，請改用 **\/LTCG** 及 **\/GENPROFILE** 或 **\/FASTGENPROFILE**。  
  
 從經過檢測的回合收集而來的資料，會用於建立最佳化的映像。如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。此選項的簡短形式為 \/LTCG:PGI。  
  
 :PGOPTIMIZE \(選擇性\)  
 此選項已被取代。若要建置最佳化的映像，請改用 **\/LTCG** 及 **\/USEPROFILE**。如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。此選項的簡短形式為 \/LTCG:PGO。  
  
 :PGOPTIMIZE \(選擇性\)  
 此選項已被取代。若要建置最佳化的映像，請改用 **\/LTCG** 及 **\/USEPROFILE**。如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。此選項的簡短形式為 \/LTCG:PGU。  
  
 \/LTCG 選項會指示連結器呼叫編譯器並執行整個程式最佳化。您也可以執行特性指引最佳化。如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。  
  
 除了下列例外之外，若舊版之 \/LTCG 與 \/GENPROFILE 選項的 PGO 初始化組合未指定 \/LTCG 與 \/USEPROFILE 的 PGO 組合，您便無法將連結器選項加入其中：  
  
-   [\/BASE](../../build/reference/base-base-address.md)  
  
-   [\/FIXED](../../build/reference/fixed-fixed-base-address.md)  
  
-   \/LTCG  
  
-   [\/MAP](../../build/reference/map-generate-mapfile.md)  
  
-   [\/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)  
  
-   [\/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)  
  
-   [\/OUT](../../build/reference/out-output-file-name.md)  
  
-   [\/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)  
  
-   [\/PDB](../../build/reference/pdb-use-program-database.md)  
  
-   [\/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)  
  
-   [\/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)  
  
-   [\/VERBOSE](../../build/reference/verbose-print-progress-messages.md)  
  
 當您使用 \/LTCG 與 \/USEPROFILE 執行建置時，無須與 \/LTCG 及 \/GENPROFILE 選項一起指定連結器選項，就能初始化 PGO；這些選項已隱含其中。  
  
 本主題的其餘部分會就連結時產生程式碼來討論 \/LTCG。  
  
 [\/GL](../../build/reference/gl-whole-program-optimization.md) 隱含了 \/LTCG。  
  
 若連結器接獲傳遞使用 **\/GL** 或 MSIL 模組 \(請參閱 [.netmodule 檔做為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)\) 所編譯的模組，會叫用連結時產生程式碼。即使您在傳遞 **\/GL** 或 MSIL 模組給連結器時未明確指定 **\/LTCG**，連結器最終還是會偵測此參數，然後使用 **\/LTCG** 重新啟動連結。若您能在傳遞 **\/GL** 與 MSIL 模組給連結器時明確指定 **\/LTCG**，將可獲得最快的建置效能。  
  
 如需更快的效能，請使用 **\/LTCG:INCREMENTAL**。此選項會指示連結器只重新最佳化會受到來源檔案變更影響的檔案集，而不是重新最佳化整個專案。這可以大幅減少所需的連結時間。這與累加連結的選項不同。  
  
 當 **\/LTCG** 搭配 [\/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) 一起使用時無效。。  
  
 當 **\/LTCG** 用於連結連結使用 [\/Og](../../build/reference/og-global-optimizations.md)、[\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)、[\/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 或 [\/Ox](../../build/reference/ox-full-optimization.md) 所編譯的連結模組時，會執行下列最佳化：  
  
-   跨模組內嵌  
  
-   跨程序暫存器配置 \(僅限 64 位元作業系統\)  
  
-   自訂呼叫慣例 \(僅限 x86\)  
  
-   小型 TLS 置換 \(僅限 x86\)  
  
-   堆疊雙重對齊 \(僅限 x86\)  
  
-   改記憶體去除混淆 \(為全域變數及輸入參數提供更好的介入資訊\)  
  
> [!NOTE]
>  連結器會決定編譯每個函式時所要使用的最佳化方式，並在連結時套用相同的最佳化方式。  
  
 使用 **\/LTCG** 及 **\/Ogt** 會造成雙重對齊最佳化。  
  
 若指定 **\/LTCG** 及 **\/Ogs**，便不會執行雙重對齊。若大應用程式中大部分函式的編譯目的為速度，少數一些的編譯目的為大小 \(例如使用 [最佳化](../../preprocessor/optimize.md) pragma\)，當這些函式需要雙重對齊時，編譯器會雙重對齊因大小目的而編譯的函式。  
  
 若編譯器能夠識函式所有的呼叫站台，編譯器將會忽略對函式發出的明確呼叫慣例修飾詞，並嘗試最佳化函式的呼叫慣例：  
  
-   在暫存器中傳遞參數  
  
-   重新排序對齊參數  
  
-   移除未使用的參數  
  
 若是透過函式指標呼叫函式，或是從使用 **\/GL** 所編譯的模組外部呼叫函式，編譯器便不會嘗試最佳化函式的呼叫慣例。  
  
> [!NOTE]
>  若是使用 **\/LTCG** 並重新定義 mainCRTStartup，可能會造成應用程式出現無法預期的行為，並牽連全域物件初始化之前所執行的使用者程式碼。有三種方式可以處理此問題：不重新定義 mainCRTStartup、不使用 **\/LTCG** 編譯包含 mainCRTStartup 的檔案，或以靜態方式初始化全域變數及物件。  
  
## \/LTCG 與 MSIL 模組  
 以 [\/GL](../../build/reference/gl-whole-program-optimization.md) 和 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 編譯的模組可以在指定 **\/LTCG** 時用做連結器的輸入。  
  
-   **\/LTCG** 可接受原生物件檔案、原生\/Managed 物件檔案混合 \(使用 **\/clr** 編譯\)、純物件檔案 \(使用 **\/clr:pure** 編譯\) 及安全物件檔案 \(使用 **\/clr:safe** 編譯\)。  
  
-   **\/LTCG** 可以接受安全的 .net 模組，這類模組可以在 Visual C\+\+ 中使用 **\/clr:safe \/LN**，以及在其他 Visual Studio 編譯器中使用 **\/target:module** 建立。**\/clr** 不接受使用 **\/clr:pure** 或 **\/LTCG** 產生的 .netmodule。  
  
-   \/LTCG:PGI 不接受使用 **\/GL** 和 **\/clr** 編譯的原生模組，或純模組 \(使用 **\/clr:pure** 產生的\)  
  
#### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。 請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**組態屬性**\] 資料夾。  
  
3.  選取 \[**一般**\] 屬性頁。  
  
4.  修改**整個程式最佳化**屬性。  
  
 您也可以將 **\/LTCG** 套用至特定組建，方式是選擇功能表列上的 \[**建置**\]、\[**特性指引最佳化**\]，或是在專案的捷徑功能表上選擇其中一個特性指引最佳化選項。  
  
#### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)