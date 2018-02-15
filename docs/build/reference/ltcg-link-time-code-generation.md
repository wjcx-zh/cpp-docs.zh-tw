---
title: "-LTCG （連結時間程式碼產生） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
dev_langs:
- C++
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69e67755ce5015cdd63ad36625e71380a303d2d4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (連結時間產生程式碼)
```  
/LTCG[:INCREMENTAL|:NOSTATUS|:STATUS|:OFF|:PGINSTRUMENT|:PGOPTIMIZE|:PGUPDATE]  
```  
  
## <a name="remarks"></a>備註  
 : INCREMENTAL （選擇性）  
 指定的連結器僅適用於整個程式最佳化或連結時間程式碼產生 (LTCG) 受影響的編輯，而不是整個專案的檔案集。 根據預設，此旗標未設定當指定 /LTCG 時，並使用整個程式最佳化連結整個專案。  
  
 : NOSTATUS &#124;: STATUS （選擇性）  
 指定連結器是否會顯示進度指示器，以顯示連結完成的百分比。 根據預設，不顯示這項狀態資訊。  
  
 : OFF （選擇性）  
 停用連結時產生程式碼。 此行為是未在命令列上指定 /LTCG 相同。  
  
 : PGINSTRUMENT （選擇性）  
 此選項已被取代。 請改用**/LTCG**和**/GENPROFILE**或**/FASTGENPROFILE**產生經過檢的組建進行特性指引最佳化。  
  
 從檢測測試回合所收集的資料用來建立最佳化的映像。 如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。 這個選項的簡短形式為 /ltcg: pgi。  
  
 : PGOPTIMIZE （選擇性）  
 此選項已被取代。 請改用**/LTCG**和**/USEPROFILE**建置最佳化的映像。 如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。 這個選項的簡短形式為 /ltcg: pgo 進行。  
  
 : PGOPTIMIZE （選擇性）  
 此選項已被取代。 請改用**/LTCG**和**/USEPROFILE**建置最佳化的映像。 如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。 這個選項的簡短形式是 /LTCG:PGU。  
  
 /LTCG 選項是告訴連結器呼叫編譯器並且執行整個程式的最佳化。 您也可以執行特性指引最佳化。 如需詳細資訊，請參閱[特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。  
  
 有下列例外狀況中，您無法將連結器選項新增 /LTCG 和先前的 PGO 初始化組合 /LTCG 和 /GENPROFILE 選項中未指定 /USEPROFILE 的 PGO 組合：  
  
-   [/BASE](../../build/reference/base-base-address.md)  
  
-   [/FIXED](../../build/reference/fixed-fixed-base-address.md)  
  
-   /LTCG  
  
-   [/MAP](../../build/reference/map-generate-mapfile.md)  
  
-   [/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)  
  
-   [/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)  
  
-   [/OUT](../../build/reference/out-output-file-name.md)  
  
-   [/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)  
  
-   [/PDB](../../build/reference/pdb-use-program-database.md)  
  
-   [/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)  
  
-   [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)  
  
-   [/VERBOSE](../../build/reference/verbose-print-progress-messages.md)  
  
 任何的已指定了 /LTCG 連結器選項和 /GENPROFILE 選項，以初始化 PGO 不需要指定當您建立使用 /LTCG 和 /USEPROFILE;它們被隱含的。  
  
 本主題的其餘部分從連結時產生程式碼方面討論 /LTCG。  
  
 /LTCG 與隱含[/GL](../../build/reference/gl-whole-program-optimization.md)。  
  
 連結器叫用連結時產生程式碼，如果在使用已編譯的模組**/GL**或 MSIL 模組 (請參閱[.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md))。 如果您未明確指定**/LTCG**傳遞時， **/GL**或 MSIL 模組給連結器連結器最後會偵測出這和重新啟動連結使用**/LTCG**。 明確指定**/LTCG**傳遞時， **/GL**和 MSIL 模組給連結器可能的最快建置效能。  
  
 為了更快的效能，使用**/LTCG： 累加**。 此選項會指示連結器只重新最佳化會受到來源檔案變更影響的檔案集，而不是重新最佳化整個專案。 這可以大幅減少所需的連結時間。 這不是相同的選項，累加連結。  
  
 **/LTCG**不能搭配[/增量](../../build/reference/incremental-link-incrementally.md)。  
  
 當**/LTCG**用來連結使用所編譯模組[/Og](../../build/reference/og-global-optimizations.md)， [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)， [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)，或[/Ox](../../build/reference/ox-full-optimization.md)，會執行下列最佳化：  
  
-   跨模組的內嵌  
  
-   跨暫存器配置 （僅限 64 位元作業系統）  
  
-   自訂呼叫慣例 (僅限 x86)  
  
-   小型 TLS 替代 (僅限 x86)  
  
-   堆疊雙重對齊 (僅限 x86)  
  
-   已改進的記憶體去除混淆 （更好資訊的全域變數和輸入的參數）  
  
> [!NOTE]
>  連結器判斷哪一個最佳化已用來編譯每個函式，並在連結時間套用相同的最佳化。  
  
 使用**/LTCG**和**/Ogt**會造成雙重對齊最佳化。  
  
 如果**/LTCG**和**/Ogs**指定，就不會執行雙重對齊。 如果大部分的應用程式中的函式會針對速度編譯，與針對大小編譯的幾個函式 (例如，藉由使用[最佳化](../../preprocessor/optimize.md)pragma)，編譯器會雙重對齊，如果它們呼叫大小最佳化的函式需要雙重對齊的函式。  
  
 如果編譯器能夠識別函式的所有呼叫位置，編譯器會忽略函式上的明確呼叫慣例修飾詞，並嘗試將函式的呼叫慣例最佳化：  
  
-   在暫存器中傳遞參數  
  
-   對齊方式重新排列參數  
  
-   移除未使用的參數  
  
 如果函式透過函式指標加以呼叫，或從呼叫函式使用編譯的模組之外**/GL**，編譯器不會嘗試將函式的呼叫慣例最佳化。  
  
> [!NOTE]
>  如果您使用**/LTCG**並重新定義 mainCRTStartup，您的應用程式可以有無法預期的行為與全域物件初始化以前執行之使用者程式碼相關。  若要解決此問題的三種方式： 無法重新定義 mainCRTStartup、 不會編譯包含 mainCRTStartup 的檔案**/LTCG**，或以靜態方式初始化全域變數和物件。  
  
## <a name="ltcg-and-msil-modules"></a>/LTCG 與 MSIL 模組  
 以 [/GL](../../build/reference/gl-whole-program-optimization.md) 和 [/clr](../../build/reference/clr-common-language-runtime-compilation.md) 編譯的模組可以在指定 **/LTCG** 時用做連結器的輸入。  
  
-   **/LTCG**可接受原生物件的檔案和混合原生 /managed 物件檔案 (使用編譯的**/clr**)。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
-   /Ltcg: pgi 不接受使用所編譯的原生模組**/GL**和**/clr**  
  
#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [ **屬性頁** ] 對話方塊。 請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 [ **組態屬性** ] 資料夾。  
  
3.  選取 [ **一般** ] 屬性頁。  
  
4.  修改 **整個程式最佳化** 屬性。  
  
 您也可以將 **/LTCG** 套用至特定組建，方式是選擇功能表列上的 [ **建置**]、[ **特性指引最佳化** ]，或是在專案的捷徑功能表上選擇其中一個特性指引最佳化選項。  
  
#### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)