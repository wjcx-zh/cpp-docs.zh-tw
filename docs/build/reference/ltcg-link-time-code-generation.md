---
title: /LTCG (連結時產生程式碼)
description: MSVC 連結器選項/LTCG 可提供整個程式優化的連結時產生程式碼。
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
ms.openlocfilehash: 6c0009e5236f33119ed411dc81ce6a4385f21a2a
ms.sourcegitcommit: f7fbdc39d73e1fb3793c396fccf7a1602af7248b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2020
ms.locfileid: "91662264"
---
# <a name="ltcg-link-time-code-generation"></a>`/LTCG` (連結時產生程式碼) 

用 **`/LTCG`** 來執行整個程式的優化，或建立特性指引優化 (PGO) 檢測、執行定型，以及建立特性指引優化的組建。

## <a name="syntax"></a>語法

> **`/LTCG`**[**`:`**{**`INCREMENTAL`**|**`NOSTATUS`**|**`STATUS`**|**`OFF`**}]

這些選項已自 Visual Studio 2015 起淘汰：

> **`/LTCG:`**{**`PGINSTRUMENT`**|**`PGOPTIMIZE`**|**`PGUPDATE`**}

### <a name="arguments"></a>引數

**`INCREMENTAL`**<br/>
 (選擇性) 指定連結器只會將整個程式優化或連結時產生程式碼 (LTCG) 套用至受編輯影響的檔案，而不是整個專案。 根據預設，指定時不會設定此旗標 **`/LTCG`** ，而且整個專案是使用整個程式優化來連結。

**`NOSTATUS`** &#124; **`STATUS`**<br/>
(選擇性) 指定連結器是否會顯示進度指示器，以顯示連結完成的百分比。 預設不會顯示此狀態資訊。

**`OFF`**<br/>
(選擇性) 停用連結時產生程式碼。 此行為與在 **`/LTCG`** 命令列上未指定時相同。

**`PGINSTRUMENT`**<br/>
(選擇性) 此選項已自 Visual Studio 2015 起淘汰。 請改用 **`/LTCG`** 和[ `/GENPROFILE` `/FASTGENPROFILE` 或](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)來產生特性指引優化的檢測組建。 從檢測測試回合所收集的資料用來建立最佳化的映像。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。 此選項的簡短形式為 **`/LTCG:PGI`** 。

**`PGOPTIMIZE`**<br/>
(選擇性) 此選項已自 Visual Studio 2015 起淘汰。 請改用 **`/LTCG`** 和  [`/USEPROFILE`](useprofile.md) 來建立優化的映射。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。 此選項的簡短形式為 **`/LTCG:PGO`** 。

**`PGUPDATE`**<br/>
(選擇性) 此選項已自 Visual Studio 2015 起淘汰。 請改用 **`/LTCG`** 和  **`/USEPROFILE`** 來重建優化的映射。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。 此選項的簡短形式為 **`/LTCG:PGU`** 。

## <a name="remarks"></a>備註

**`/LTCG`** 選項會告訴連結器呼叫編譯器，並執行整個程式的優化。 您也可以執行特性指引最佳化。 如需詳細資訊，請參閱[特性指引最佳化](../profile-guided-optimizations.md)。

但有下列例外狀況，您就無法將連結器選項加入至 **`/LTCG`** 和 **`/USEPROFILE`** 選項先前的 pgo 初始化組合中未指定的 PGO 組合 **`/LTCG`** **`/GENPROFILE`** ：

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

**`/LTCG`** **`/GENPROFILE`** 當您使用和來建立時，不需要指定連同和選項一起指定的任何連結器選項，而是 **`/LTCG`** **`/USEPROFILE`** 隱含的。

本文的其餘部分將討論完成的連結時間程式碼產生 **`/LTCG`** 。

**`/LTCG`** 是隱含的 [`/GL`](gl-whole-program-optimization.md) 。

連結器會在傳遞使用編譯的模組或 MSIL 模組時，叫用連結時產生程式碼， **`/GL`** (查看檔案[ `.netmodule` 做為連結器輸入](netmodule-files-as-linker-input.md)) 。 如果您未明確指定 **`/LTCG`** 當您傳遞 **`/GL`** 或 MSIL 模組給連結器時，連結器最終會偵測到這種情況，並使用重新開機連結 **`/LTCG`** 。 **`/LTCG`** 當您將 **`/GL`** 和 MSIL 模組傳遞至連結器，以取得最快速的組建效能時，請明確指定。

如需更快的效能，請使用 **`/LTCG:INCREMENTAL`** 。 此選項會指示連結器只重新重新優化受到來源檔案變更影響的檔案，而不是整個專案。 這個選項可以大幅減少所需的連結時間。 此選項與 [增量連結](incremental-link-incrementally.md)的選項不同。

**`/LTCG`** 與搭配使用無效 [`/INCREMENTAL`](incremental-link-incrementally.md) 。

當 **`/LTCG`** 用來連結使用 [`/Og`](og-global-optimizations.md) 、、或所編譯的模組時 [`/O1`](o1-o2-minimize-size-maximize-speed.md) [`/O2`](o1-o2-minimize-size-maximize-speed.md) [`/Ox`](ox-full-optimization.md) ，會執行下列優化：

- 跨模組內嵌

- 跨程序的暫存器配置 (僅限 64 位元作業系統)

- 自訂呼叫慣例 (僅限 x86)

- 小型的 TLS 置換 (僅限 x86)

- 堆疊雙重對齊 (僅限 x86)

- 改進記憶體去除混淆 (為全域變數及輸入參數提供更好的介入資訊)

> [!NOTE]
> 連結器會決定編譯每個函式時所要使用的最佳化方式，並在連結時套用相同的最佳化方式。

使用 **`/LTCG`** 和 **`/O2`** 會造成雙重對齊優化。

如果 **`/LTCG`** **`/O1`** 指定了和，則不會執行雙重對齊。 如果應用程式中大部分的函式都是針對速度編譯，則有一些針對大小編譯的函式 (例如，藉由使用 [`optimize`](../../preprocessor/optimize.md) pragma) ，編譯器會在呼叫需要雙重對齊的函式時，將已針對大小優化的函式加倍對齊。

如果編譯器能夠識別函式的所有呼叫位置，編譯器會忽略函式上的明確呼叫慣例修飾詞，並嘗試將函式的呼叫慣例最佳化：

- 在暫存器內傳遞參數

- 重新排列參數以對齊

- 移除未使用的參數

如果函式是透過函式指標呼叫，或從使用編譯的模組之外呼叫函式， **`/GL`** 則編譯器不會嘗試將函式的呼叫慣例優化。

> [!NOTE]
> 如果您使用 **`/LTCG`** 和重新定義 `mainCRTStartup` ，您的應用程式可能會有無法預期的行為，這些行為會與全域物件初始化之前執行的使用者程式碼相關。 有三種方式可以處理此問題：不重新定義 `mainCRTStartup` 、不使用來編譯包含的檔案， `mainCRTStartup` 或以靜態方式 **`/LTCG`** 初始化全域變數和物件。

### <a name="ltcg-and-msil-modules"></a>`/LTCG` 和 MSIL 模組

使用編譯的模組 [`/GL`](gl-whole-program-optimization.md) [`/clr`](clr-common-language-runtime-compilation.md) 可以在指定時當做連結器的輸入使用 **`/LTCG`** 。

- **`/LTCG`** 可以接受原生物件檔案，以及使用)  (編譯的混合原生/managed 物件檔案 **`/clr`** 。 **`/clr:pure`** 和 **`/clr:safe`** 編譯器選項在 Visual Studio 2015 中已被取代，Visual Studio 2017 和更新版本不支援。

- **`/LTCG:PGI`** 不接受使用和編譯的原生模組 **`/GL`****`/clr`**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **一般**] 屬性頁。

1. 修改 **整個程式最佳化** 屬性。

您也可以在 **`/LTCG`** 功能表列上選擇 [**組建**  >  **設定檔指引優化**]，或是在專案的快捷方式功能表上選擇其中一個特性指引優化選項，以套用至特定組建。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)\
[MSVC 連結器選項](linker-options.md)
