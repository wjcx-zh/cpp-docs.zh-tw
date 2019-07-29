---
title: HLSL 屬性頁
ms.date: 07/24/2019
ms.assetid: 0c65f5ec-a2a5-4f5b-8d4c-fa57113a5a1d
f1_keywords:
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.SuppressStartupBanner
- VC.Project.FXCompilerTool.EntryPointName
- VC.Project.FXCompilerTool.TreatWarningAsError
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.AllResourcesBound
- VC.Project.FXCompilerTool.EnableUnboundedDescriptorTables
- VC.Project.FXCompilerTool.SetRootSignature
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.AdditionalOptionsPage
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.AssemblerOutputFile
- VC.Project.FXCompilerTool.CompileD2DCustomEffect
- VC.Project.FXCompilerTool.MultiProcFXC
ms.openlocfilehash: a45ae433e5adaa8aeaf32215d4af7ad0a247af04
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606406"
---
# <a name="hlsl-compiler-property-pages"></a>HLSL 編譯器屬性頁

您可以使用 HLSL 編譯器 (fxc.exe) 屬性頁，設定個別 HLSL 著色器檔案的建置方式。 您也可以使用 [**命令列**] 屬性頁的 [**其他選項**] 屬性, 指定 HLSL 編譯器的命令列引數;這包括無法使用 HLSL 屬性頁的其他屬性來設定的引數。 如需 HLSL 編譯器的資訊，請參閱 [Effect-Compiler Tool](https://go.microsoft.com/fwlink/p/?LinkID=258285&clcid=0x409) (效果編譯器工具)

## <a name="hlsl-general-property-page"></a>HLSL 一般屬性頁

### <a name="additional-include-directories"></a>其他 Include 目錄

指定一或多個要新增至 Include 路徑中的目錄；如有多個目錄，請使用分號加以分隔。 (/I [路徑])

### <a name="entrypoint-name"></a>進入點名稱

指定著色器的進入點名稱 (/E [名稱])

### <a name="disable-optimizations"></a>停用優化

[是 (/Od)] 可停用最佳化；否則為 [否]。 根據預設，[偵錯] 組態的值是 [是 (/Od)]，而 [發行] 組態的值是 [否]。

HLSL 編譯器的 **/Od** 命令列引數會隱含地套用 **/Gfp** 命令列引數，但輸出可能不同於同時明確傳遞 **/Od** 和 **/Gfp** 命令列引數所產生的輸出。

### <a name="enable-debugging-information"></a>啟用調試資訊

[是 (/Zi)] 可啟用偵錯資訊；否則為 [否]。 根據預設，[偵錯] 組態的值是 [是 (/Zi)]，而 [發行] 組態的值是 [否]。

### <a name="shader-type"></a>著色器類型

指定著色器種類。 不同種類的著色器會實作圖形管線的不同部分。 特定種類的著色器僅可用於較新的著色器模型 (其由 [著色器模型] 屬性指定)。例如，在著色器模型 5 中引入了計算著色器。

此屬性對應於 HLSL 編譯器的 **/T \[type]_\[model]** 命令列引數的 **\[type]** 部分。 [著色器模型] 屬性則會指定引數的 **[model]** 部分。

**做**

- **Effect**
- **頂點著色器**
- **像素著色器**
- **幾何著色器**
- **輪廓著色器**
- **網域著色器**
- **計算著色器**
- **程式庫**
- **產生根簽章物件**

### <a name="shader-model"></a>著色器模型

指定著色器模型。 不同的著色器模型具有不同的功能。 一般情況下，較新的著色器模型會提供擴充功能，但需要更先進的圖形硬體才能執行著色器程式碼。 特定種類的著色器 (其由 [著色器類型] 屬性指定) 僅可用於較新的著色器模型；例如，在著色器模型 5 中引入了計算著色器。

此屬性對應於 HLSL 編譯器的 **/T \[type]_\[model]** 命令列引數的 **\[model]** 部分。 [著色器類型] 屬性則會指定引數的 **[type]** 部分。

### <a name="all-resources-bound"></a>所有系結的資源

編譯器會假設在著色器執行期間, 著色器可能參考的所有資源都已系結且處於良好狀態 (/all_resources_bound)。 適用於著色器模型 5.1 (含) 以上版本。

### <a name="enable-unbounded-descriptor-tables"></a>啟用未系結的描述項資料表

通知編譯器, 著色器可能包含具有未系結範圍 (/enable_unbounded_descriptor_tables) 之資源陣列的宣告。 適用於著色器模型 5.1 (含) 以上版本。

### <a name="set-root-signature"></a>設定根簽章

將根簽章附加至著色器位元組路徑 (/setrootsignature)。 適用於著色器模型 5.0 (含) 以上版本。

### <a name="preprocessor-definitions"></a>前置處理器定義

新增一或多個要套用至 HLSL 原始程式碼檔案的前置處理器符號定義。 請使用分號來分隔這些符號定義。

此屬性對應於 HLSL 編譯器的 **/D \[definitions]** 命令列引數。

### <a name="compile-a-direct2d-custom-pixel-shader-effect"></a>編譯 Direct2D 自訂圖元著色器效果

編譯包含像素著色器的 Direct2D 自訂效果。 請勿用於頂點或計算自訂效果。

### <a name="multi-processor-compilation"></a>多處理器編譯

同時執行多個實例。

## <a name="advanced-property-page"></a>Advanced 屬性頁

### <a name="suppress-startup-banner"></a>隱藏啟動橫幅

隱藏程式啟始資訊及資訊訊息。 /nologo

### <a name="treat-warnings-as-errors"></a>將警告視為錯誤

將所有編譯器警告視為錯誤。 若是新專案，建議在所有編譯中使用 /WX；解決所有警告時，才能將難以找出的程式碼缺失降至最低。

## <a name="output-files-property-page"></a>輸出檔案屬性頁

### <a name="header-variable-name"></a>標頭變數名稱

在標頭檔中指定變數名稱的名稱 (/Vn [name])

### <a name="header-file-name"></a>標頭檔名稱

指定包含目的碼的標頭檔名稱。 (/Fh [名稱])

### <a name="object-file-name"></a>物件檔案名稱

指定目的檔的名稱。 (/Fo [名稱])

### <a name="assembler-output"></a>組合器輸出

指定組合語言輸出檔案的內容。 (/Fc,/Fx)

**做**

- **無清單**-沒有清單。
- **僅限元件清單**-元件程式碼檔案
- 組譯程式**代碼和十六進位**組解碼和十六進位清單檔

### <a name="assembler-output-file"></a>組合器輸出檔

指定元件程式代碼清單檔的檔案名

## <a name="see-also"></a>另請參閱

[C++專案屬性頁參考](property-pages-visual-cpp.md)<br>
[命令列屬性頁](command-line-property-pages.md)<br>
[編譯著色器](https://go.microsoft.com/fwlink/p/?LinkID=258284&clcid=0x409)
