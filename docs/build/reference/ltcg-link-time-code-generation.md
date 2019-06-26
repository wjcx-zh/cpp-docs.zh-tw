---
title: /LTCG (連結時間產生程式碼)
ms.date: 05/16/2019
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
ms.openlocfilehash: 1e33d62694fe782b1a1719fa3c5a36c6fb04670a
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400623"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (連結時間產生程式碼)

使用 **/LTCG** 來執行整個程式的最佳化，或建立特性指引最佳化 (PGO) 檢測、執行訓練及建立特性指引最佳化組建。

## <a name="syntax"></a>語法

> **/LTCG**[ **:** {**INCREMENTAL**|**NOSTATUS**|**STATUS**|**OFF**}]

這些選項已自 Visual Studio 2015 起淘汰：

> **/LTCG:** {**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}

### <a name="arguments"></a>引數

**INCREMENTAL**<br/>
(選擇性) 指定的連結器僅將整個程式最佳化或連結時產生程式碼 (LTCG) 套用到受編輯影響的檔案集，而不是套用到整個專案。 根據預設，指定 **/LTCG** 時不會設定此旗標，而整個專案會使用完整程式最佳化來連結。

**NOSTATUS** &#124; **STATUS**<br/>
(選擇性) 指定連結器是否會顯示進度指示器，以顯示連結完成的百分比。 根據預設，不顯示這項狀態資訊。

**OFF**<br/>
(選擇性) 停用連結時產生程式碼。 此行為如同未在命令列上指定 **/LTCG**。

**PGINSTRUMENT**<br/>
(選擇性) 此選項已自 Visual Studio 2015 起淘汰。 請改用 **/LTCG**和 [/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) 來產生特性指引最佳化的檢測組建。 從檢測測試回合所收集的資料用來建立最佳化的映像。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。 此選項的簡短形式為 **/LTCG:PGI**。

**PGOPTIMIZE**<br/>
(選擇性) 此選項已自 Visual Studio 2015 起淘汰。 請改用 **/LTCG** 和 [/USEPROFILE](useprofile.md) 來建置最佳化映像。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。 此選項的簡短形式為 **/LTCG:PGO**。

**PGUPDATE**<br/>
(選擇性) 此選項已自 Visual Studio 2015 起淘汰。 請改用 **/LTCG** 和 **/USEPROFILE** 來重建最佳化映像。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。 此選項的簡短形式為 **/LTCG:PGU**。

## <a name="remarks"></a>備註

**/LTCG** 選項是告訴連結器呼叫編譯器並且執行整個程式的最佳化。 您也可以執行特性指引最佳化。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。

在下列例外狀況中，如果您未在前一個 **/LTCG** 與 **/GENPROFILE** 選項的 PGO 初始化組合中指定 **/LTCG** 與 **/USEPROFILE** 的 PGO 組合，您將無法將連結器選項新增至該 PGO 組合：

- [/BASE](base-base-address.md)

- [/FIXED](fixed-fixed-base-address.md)

- **/LTCG**

- [/MAP](map-generate-mapfile.md)

- [/MAPINFO](mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](nologo-suppress-startup-banner-linker.md)

- [/OUT](out-output-file-name.md)

- [/PGD](pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](pdb-use-program-database.md)

- [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)

- [/STUB](stub-ms-dos-stub-file-name.md)

- [/VERBOSE](verbose-print-progress-messages.md)

為初始化 PGO 而與 **/LTCG** 和 **/GENPROFILE** 選項一起指定的任何連結器選項，皆無須在使用 **/LTCG** 和 **/USEPROFILE** 進行建置時加以指定；這些選項已包含在內。

本文的其餘部分將從連結時產生程式碼方面討論 **/LTCG**。

**/LTCG** 隱含在 [/GL](gl-whole-program-optimization.md) 之中。

如果將使用 **/GL** 編譯的模組或 MSIL 模組傳遞給連結器，連結器就會叫用連結時產生程式碼 (請參閱[作為連結器輸入的 .netmodule 檔案](netmodule-files-as-linker-input.md))。 即使您在傳遞 **/GL** 或 MSIL 模組給連結器時未明確指定 **/LTCG**，連結器最終還是會偵測此參數，然後使用 **/LTCG** 重新啟動連結。 傳遞 **/GL** 和 MSIL 模組給連結器時，明確指定 **/LTCG**，將可盡可能達到最快的建置效能。

如需更快的效能，可使用 **/LTCG:INCREMENTAL**。 此選項會指示連結器只重新最佳化會受到來源檔案變更影響的檔案集，而不是重新最佳化整個專案。 這可以大幅減少所需的連結時間。 此選項與累加連結不同。

**/LTCG** 不能搭配 [/INCREMENTAL](incremental-link-incrementally.md) 使用。

當 **/LTCG** 用來連結使用 [/Og](og-global-optimizations.md)、[/O1](o1-o2-minimize-size-maximize-speed.md)、[/O2](o1-o2-minimize-size-maximize-speed.md) 或 [/Ox](ox-full-optimization.md) 編譯的模組時，會執行下列最佳化：

- 跨模組內嵌

- 跨程序的暫存器配置 (僅限 64 位元作業系統)

- 自訂呼叫慣例 (僅限 x86)

- 小型的 TLS 置換 (僅限 x86)

- 堆疊雙重對齊 (僅限 x86)

- 改進記憶體去除混淆 (為全域變數及輸入參數提供更好的介入資訊)

> [!NOTE]
> 連結器會決定編譯每個函式時所要使用的最佳化方式，並在連結時套用相同的最佳化方式。

使用 **/LTCG** 及 **/Ogt** 會造成雙重對齊最佳化。

若指定 **/LTCG** 及 **/Ogs**，便不會執行雙重對齊。 如果應用程式中大部分函式都是針對速度編譯，只有少數幾個函式是針對大小編譯的 (例如，經由使用 [optimize](../../preprocessor/optimize.md) pragma)，如果這些針對大小最佳化的函式呼叫需要雙重最佳化的函式，編譯器會雙重對齊這些函式。

如果編譯器能夠識別函式的所有呼叫位置，編譯器會忽略函式上的明確呼叫慣例修飾詞，並嘗試將函式的呼叫慣例最佳化：

- 在暫存器內傳遞參數

- 重新排列參數以對齊

- 移除未使用的參數

如果函式是透過函式指標加以呼叫，或如果函式在以 **/GL** 編譯的模組之外呼叫，編譯器不會嘗試將函式的呼叫慣例最佳化。

> [!NOTE]
> 如果您使用 **/LTCG** 並且重新定義 `mainCRTStartup`，您的應用程式可能會發生與全域物件初始化以前執行之使用者程式碼相關的無法預期行為。 有三種方式可以處理此問題：不重新定義 `mainCRTStartup`、不使用 **/LTCG** 編譯包含 `mainCRTStartup` 的檔案，或以靜態方式初始化全域變數及物件。

### <a name="ltcg-and-msil-modules"></a>/LTCG 與 MSIL 模組

以 [/GL](gl-whole-program-optimization.md) 和 [/clr](clr-common-language-runtime-compilation.md) 編譯的模組可以在指定 **/LTCG** 時用做連結器的輸入。

- **/LTCG** 可以接受原生物件檔案，以及混合的原生/受控物件檔案 (使用 **/clr** 編譯)。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代，而且無法在 Visual Studio 2017 及更新版本中使用。

- **/LTCG:PGI** 不接受使用 **/GL** 和 **/clr** 編譯的原生模組

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [組態屬性]   > [一般]  屬性頁。

1. 修改 **整個程式最佳化** 屬性。

您也可以將 **/LTCG** 套用至特定組建，方式是選擇功能表列上的 [組建]   > [特性指引最佳化]  ，或是在專案的捷徑功能表上選擇其中一個特性指引最佳化選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
