---
title: /LTCG (連結時產生程式碼)
description: MSVC 連結器選項/LTCG 可為整個程式優化提供連結時間程式碼產生。
ms.date: 07/08/2020
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
ms.openlocfilehash: c954794d6d0fd087eee74ebb7e86d77b89a9a8fc
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180795"
---
# <a name="ltcg-link-time-code-generation"></a>`/LTCG` (連結時產生程式碼) 

用 **`/LTCG`** 來執行整個程式優化，或建立特性指引優化 (PGO) 檢測、執行定型，以及建立特性指引優化的組建。

## <a name="syntax"></a>語法

> **`/LTCG`**[**`:`**{**`INCREMENTAL`**|**`NOSTATUS`**|**`STATUS`**|**`OFF`**}]

這些選項已自 Visual Studio 2015 起淘汰：

> **`/LTCG:`**{**`PGINSTRUMENT`**|**`PGOPTIMIZE`**|**`PGUPDATE`**}

### <a name="arguments"></a>引數

**`INCREMENTAL`**<br/>
 (選擇性) 指定連結器只會將整個程式優化或連結時間程式碼產生 (LTCG) 套用至受編輯影響的檔案，而不是整個專案。 根據預設，當指定時，不會設定此旗標 **`/LTCG`** ，而整個專案會使用整個程式優化進行連結。

**`NOSTATUS`**&#124;**`STATUS`**<br/>
(選擇性) 指定連結器是否會顯示進度指示器，以顯示連結完成的百分比。 根據預設，不會顯示此狀態資訊。

**`OFF`**<br/>
(選擇性) 停用連結時產生程式碼。 這個行為與 **`/LTCG`** 命令列上未指定時相同。

**`PGINSTRUMENT`**<br/>
(選擇性) 此選項已自 Visual Studio 2015 起淘汰。 請改用 **`/LTCG`** 和 `[/GENPROFILE` 或 `/FASTGENPROFILE` ] (genprofile-fastgenprofile-generate-profiling-instrumented-build.md) 產生特性指引優化的檢測組建。 從檢測測試回合所收集的資料用來建立最佳化的映像。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。 此選項的簡短形式為 **`/LTCG:PGI`** 。

**`PGOPTIMIZE`**<br/>
(選擇性) 此選項已自 Visual Studio 2015 起淘汰。 請改用 **`/LTCG`** 和 [`/USEPROFILE`](useprofile.md) 來建立優化的映射。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。 此選項的簡短形式為 **`/LTCG:PGO`** 。

**`PGUPDATE`**<br/>
(選擇性) 此選項已自 Visual Studio 2015 起淘汰。 請改用 **`/LTCG`** 和 **`/USEPROFILE`** 來重建優化的映射。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。 此選項的簡短形式為 **`/LTCG:PGU`** 。

## <a name="remarks"></a>備註

**`/LTCG`** 選項會指示連結器呼叫編譯器，並執行整個程式優化。 您也可以執行特性指引最佳化。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。

除了下列例外狀況以外，您無法將連結器選項新增至 **`/LTCG`** 和 **`/USEPROFILE`** 選項的 previous pgo 初始化組合中未指定的 PGO **`/LTCG`** 組合 **`/GENPROFILE`** ：

- [`/BASE`](base-base-address.md)

- [`/FIXED`](fixed-fixed-base-address.md)

- **`/LTCG`**

- [`/MAP`](map-generate-mapfile.md)

- [`/MAPINFO`](mapinfo-include-information-in-mapfile.md)

- [`/NOLOGO`](nologo-suppress-startup-banner-linker.md)

- [`/OUT`](out-output-file-name.md)

- [`/PGD`](pgd-specify-database-for-profile-guided-optimizations.md)

- [`/PDB`](pdb-use-program-database.md)

- [`/PDBSTRIPPED`](pdbstripped-strip-private-symbols.md)

- [`/STUB`](stub-ms-dos-stub-file-name.md)

- [`/VERBOSE`](verbose-print-progress-messages.md)

**`/LTCG`** **`/GENPROFILE`** 當您使用和建立時，不需要指定任何與和選項一起指定的連結器選項來初始化 PGO， **`/LTCG`** 而 **`/USEPROFILE`** 是隱含的。

本文的其餘部分將討論由完成的連結時程式碼產生 **`/LTCG`** 。

**`/LTCG`** 會隱含使用 [`/GL`](gl-whole-program-optimization.md) 。

連結器會在傳遞使用或 MSIL 模組編譯的模組時，叫用連結時產生程式碼， **`/GL`** (請參閱檔案[ `.netmodule` 做為連結器輸入](netmodule-files-as-linker-input.md)) 。 如果您未在將 **`/LTCG`** **`/GL`** 或 MSIL 模組傳遞至連結器時明確指定，連結器最後會偵測到這種情況，並使用重新開機連結 **`/LTCG`** 。 **`/LTCG`** 當您將 **`/GL`** 和 MSIL 模組傳遞給連結器以取得最快的可能組建效能時，請明確指定。

如需更快的效能，請使用 **`/LTCG:INCREMENTAL`** 。 此選項會告訴連結器僅重新重新優化受到原始程式檔變更影響的檔案，而不是整個專案。 此選項可大幅減少所需的連結時間。 此選項和[增量連結](incremental-link-incrementally.md)的選項不同。

**`/LTCG`** 與搭配使用時無效 [`/INCREMENTAL`](incremental-link-incrementally.md) 。

當 **`/LTCG`** 用來連結使用、、或所編譯的模組時， [`/Og`](og-global-optimizations.md) [`/O1`](o1-o2-minimize-size-maximize-speed.md) [`/O2`](o1-o2-minimize-size-maximize-speed.md) [`/Ox`](ox-full-optimization.md) 會執行下列優化：

- 跨模組內嵌

- 跨程序的暫存器配置 (僅限 64 位元作業系統)

- 自訂呼叫慣例 (僅限 x86)

- 小型的 TLS 置換 (僅限 x86)

- 堆疊雙重對齊 (僅限 x86)

- 改進記憶體去除混淆 (為全域變數及輸入參數提供更好的介入資訊)

> [!NOTE]
> 連結器會決定編譯每個函式時所要使用的最佳化方式，並在連結時套用相同的最佳化方式。

使用 **`/LTCG`** 和 **`/O2`** 會導致雙重對齊優化。

如果 **`/LTCG`** **`/O1`** 指定了和，則不會執行雙重對齊。 如果應用程式中大部分的函式都是針對速度編譯的，而且有一些針對大小而編譯的函式 (例如，使用 [`optimize`](../../preprocessor/optimize.md) pragma) ，則編譯器會在呼叫需要雙重對齊的函式時，針對大小優化的函式進行雙重對齊。

如果編譯器能夠識別函式的所有呼叫位置，編譯器會忽略函式上的明確呼叫慣例修飾詞，並嘗試將函式的呼叫慣例最佳化：

- 在暫存器內傳遞參數

- 重新排列參數以對齊

- 移除未使用的參數

如果函式是透過函式指標呼叫，或從使用編譯的模組外部呼叫函式， **`/GL`** 編譯器不會嘗試優化函式的呼叫慣例。

> [!NOTE]
> 如果您使用 **`/LTCG`** 和重新定義 `mainCRTStartup` ，您的應用程式可能會有與在初始化全域物件之前執行之使用者程式碼相關的無法預期行為。 有三種方式可解決此問題：不要重新定義 `mainCRTStartup` 、不使用來編譯包含的檔案 `mainCRTStartup` **`/LTCG`** ，或是靜態地初始化全域變數和物件。

### <a name="ltcg-and-msil-modules"></a>`/LTCG`和 MSIL 模組

當指定時，使用和編譯的模組 [`/GL`](gl-whole-program-optimization.md) [`/clr`](clr-common-language-runtime-compilation.md) 可以做為連結器的輸入 **`/LTCG`** 。

- **`/LTCG`** 可以接受原生物件檔，以及使用) 編譯的混合原生/managed 物件檔案 (**`/clr`** 。 **`/clr:pure`** 和 **`/clr:safe`** 編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 和更新版本中不支援。

- **`/LTCG:PGI`** 不接受使用和編譯的原生模組 **`/GL`****`/clr`**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**]  >  **[一般**] 屬性頁面。

1. 修改 **整個程式最佳化** 屬性。

您也可以在 **`/LTCG`** 功能表列上選擇 [**組建**特性  >  **指引優化**]，或是在專案的快捷方式功能表上選擇其中一個特性指引優化選項，以套用至特定組建。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)\
[MSVC 連結器選項](linker-options.md)
