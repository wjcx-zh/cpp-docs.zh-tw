---
title: /LTCG (連結時間產生程式碼)
ms.date: 03/14/2018
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
ms.openlocfilehash: 68c12cc7666da489870da1cacacc5053aeca5b51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523210"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (連結時間產生程式碼)

使用 **/LTCG**來執行整個程式最佳化，或建立設定檔指引最佳化 (PGO) 檢測、 執行訓練，並建立特性指引最佳化組建。

## <a name="syntax"></a>語法

> **/LTCG**[**:**{**INCREMENTAL**|**NOSTATUS**|**狀態**|**OFF**}]<br/>

這些選項已被取代從 Visual Studio 2015 開始：

> **/LTCG:**{**PGINSTRUMENT**|**PGOPTIMIZE**|**PGOPTIMIZE**}<br/>

### <a name="arguments"></a>引數

**增量**<br/>
（選擇性）指定，連結器僅適用於整個程式最佳化或連結時產生程式碼 (LTCG) 受影響的編輯，而不是整個專案檔案的集合。 根據預設，這個旗標未設定何時 **/LTCG**指定，則與整個專案使用連結的整個程式最佳化。

**NOSTATUS** &AMP;#124; **狀態**<br/>
（選擇性）指定連結器是否顯示進度列指示器顯示多少百分比的連結已完成。 根據預設，不顯示這項狀態資訊。

**關閉**<br/>
（選擇性）停用連結時產生程式碼。 此行為會如同在 **/LTCG**未在命令列上指定。

**PGINSTRUMENT**<br/>
（選擇性）此選項啟動 Visual Studio 2015 中已被取代。 請改用 **/LTCG**並[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)產生設定檔指引最佳化檢測的建置。 從檢測測試回合所收集的資料用來建立最佳化的映像。 如需詳細資訊，請參閱 <<c0> [ 特性指引最佳化](profile-guided-optimizations.md)。 這個選項的簡短形式 **/ltcg: pgi**。

**PGOPTIMIZE**<br/>
（選擇性）此選項啟動 Visual Studio 2015 中已被取代。 請改用 **/LTCG**並[/USEPROFILE](useprofile.md)建置最佳化的映像。 如需詳細資訊，請參閱 <<c0> [ 特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。 這個選項的簡短形式 **/ltcg: pgo 進行**。

**PGOPTIMIZE**<br/>
（選擇性）此選項啟動 Visual Studio 2015 中已被取代。 請改用 **/LTCG**並 **/USEPROFILE**重建最佳化的映像。 如需詳細資訊，請參閱 <<c0> [ 特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。 這個選項的簡短形式 **/LTCG:PGU**。

## <a name="remarks"></a>備註

**/LTCG**選項會告訴連結器呼叫編譯器並執行整個程式最佳化。 您也可以執行特性指引最佳化。 如需詳細資訊，請參閱 <<c0> [ 特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。

但有下列例外狀況，您無法將連結器選項加入的 PGO 組合 **/LTCG**並 **/USEPROFILE**的先前的 PGO 初始化組合中沒有指定， **/LTCG**並 **/GENPROFILE**選項：

- [/BASE](../../build/reference/base-base-address.md)

- [/FIXED](../../build/reference/fixed-fixed-base-address.md)

- **/LTCG**

- [/MAP](../../build/reference/map-generate-mapfile.md)

- [/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)

- [/OUT](../../build/reference/out-output-file-name.md)

- [/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](../../build/reference/pdb-use-program-database.md)

- [/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)

- [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md)

搭配使用所指定的任何連結器選項 **/LTCG**並 **/GENPROFILE**選項，以初始化 PGO 就不必指定當您使用建置 **/LTCG**和 **/USEPROFILE**; 它們隱含。

這篇文章的其餘部分將討論 **/LTCG**連結時間程式碼產生方面。

**/LTCG**就會使用隱含[/GL](../../build/reference/gl-whole-program-optimization.md)。

連結器在傳遞使用已編譯的模組，會叫用連結時產生程式碼 **/GL**或 MSIL 模組 (請參閱[.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md))。 如果您未明確指定 **/LTCG**當您傳遞 **/GL**或 MSIL 模組給連結器，連結器最後會偵測出這和使用重新啟動連結 **/LTCG**。 明確指定 **/LTCG**當您傳遞 **/GL**和 MSIL 模組給連結器可能的最快建置效能。

為了更快的效能，使用 **/LTCG： 累加**。 此選項會指示連結器只重新最佳化會受到來源檔案變更影響的檔案集，而不是重新最佳化整個專案。 這可以大幅減少所需的連結時間。 這不是使用相同的選項，做為累加連結。

**/LTCG**無效，無法搭配[/incremental](../../build/reference/incremental-link-incrementally.md)。

當 **/LTCG**用來連結使用編譯的模組[/Og](../../build/reference/og-global-optimizations.md)， [/o1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)， [/o2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)，或[/Ox](../../build/reference/ox-full-optimization.md)，會執行下列最佳化：

- 跨模組內嵌

- 跨暫存器配置 （僅 64 位元作業系統）

- 自訂呼叫慣例 (僅限 x86)

- 小型的 TLS 替代 (僅限 x86)

- Stack 雙重對齊 (僅限 x86)

- 已改進的記憶體去除混淆 （更佳的干擾資訊的全域變數和輸入的參數）

> [!NOTE]
> 連結器會決定哪些最佳化來編譯每個函式，並在連結時間套用相同的最佳化。

使用 **/LTCG**並 **/Ogt**會造成雙重對齊最佳化。

如果 **/LTCG**並 **/Ogs**指定，就不會執行雙重對齊。 如果大部分的應用程式中的函式會針對速度編譯，有幾個針對大小編譯的函式 (例如，藉由使用[最佳化](../../preprocessor/optimize.md)pragma)，編譯器會雙重對齊在呼叫針對大小進行最佳化的函式需要雙重對齊的函式。

如果編譯器能夠識別函式的所有呼叫位置，編譯器會忽略函式上的明確呼叫慣例修飾詞，並嘗試將函式的呼叫慣例最佳化：

- 在暫存器中傳遞參數

- 對齊的重新排列參數

- 移除未使用的參數

如果透過函式指標呼叫函式，或從呼叫函式會使用編譯的模組之外 **/GL**，編譯器不會嘗試將函式的呼叫慣例最佳化。

> [!NOTE]
> 如果您使用 **/LTCG** ，並重新定義`mainCRTStartup`，您的應用程式可以有無法預期的行為與全域物件會初始化之前執行的使用者程式碼。 若要解決此問題的三種方式： 不要重新定義`mainCRTStartup`，不會編譯檔案，其中包含`mainCRTStartup`利用 **/LTCG**，或以靜態方式初始化全域變數和物件。

### <a name="ltcg-and-msil-modules"></a>/LTCG 與 MSIL 模組

以 [/GL](../../build/reference/gl-whole-program-optimization.md) 和 [/clr](../../build/reference/clr-common-language-runtime-compilation.md) 編譯的模組可以在指定 **/LTCG** 時用做連結器的輸入。

- **/LTCG**可以接受原生物件檔案，而且混合原生 /managed 物件檔案 (使用編譯 **/clr**)。 **/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

- **/Ltcg: pgi**不接受使用編譯的原生模組 **/GL**和 **/clr**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **一般**屬性頁。

1. 修改 **整個程式最佳化** 屬性。

您也可以套用 **/LTCG**至所選擇的特定組建**建置** > **特性指引最佳化**功能表列上，或選擇其中一個設定檔在專案的捷徑功能表上的引導式的最佳化選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>。

## <a name="see-also"></a>另請參閱

- [設定連結器選項](../../build/reference/setting-linker-options.md)
- [連結器選項](../../build/reference/linker-options.md)
