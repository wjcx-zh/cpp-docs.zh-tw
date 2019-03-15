---
title: HLSL 屬性頁：一般
ms.date: 11/04/2016
f1_keywords:
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EntryPointName
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
ms.openlocfilehash: 0fce8a3b2a43cf05024a028a9e3325a929922abb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824758"
---
# <a name="hlsl-property-pages-general"></a>HLSL 屬性頁：一般

若要設定 HLSL 編譯器 (fxc.exe) 的下列屬性，請使用其 [一般] 屬性頁。 如需有關如何存取資訊**一般**HLSL 資料夾中的屬性頁面上看到[在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

## <a name="uielement-list"></a>UIElement 清單

- **其他 Include 目錄**

   將一或多個要目錄新增至 Include 路徑。 請使用分號來分隔這些目錄。

此屬性會對應至 **/I[path]** 命令列引數。

- **進入點名稱**

   指定著色器的進入點。 預設值為 **main**。

此屬性會對應至 **/E[name]** 命令列引數。

- [停用最佳化]

   [是 (/Od)] 可停用最佳化；否則為 [否]。 根據預設，[偵錯] 組態的值是 [是 (/Od)]，而 [發行] 組態的值是 [否]。

HLSL 編譯器的 **/Od** 命令列引數會隱含地套用 **/Gfp** 命令列引數，但輸出可能不同於同時明確傳遞 **/Od** 和 **/Gfp** 命令列引數所產生的輸出。

- **啟用偵錯資訊**

   [是 (/Zi)] 可啟用偵錯資訊；否則為 [否]。 根據預設，[偵錯] 組態的值是 [是 (/Zi)]，而 [發行] 組態的值是 [否]。

- **著色器類型**

   指定著色器種類。 不同種類的著色器會實作圖形管線的不同部分。 特定種類的著色器僅可用於較新的著色器模型 (其由 [著色器模型] 屬性指定)。例如，在著色器模型 5 中引入了計算著色器。

   此屬性對應於 HLSL 編譯器的 **/T \[type]_\[model]** 命令列引數的 **\[type]** 部分。 [著色器模型] 屬性則會指定引數的 **[model]** 部分。

- **著色器模型**

   指定著色器模型。 不同的著色器模型具有不同的功能。 一般情況下，較新的著色器模型會提供擴充功能，但需要更先進的圖形硬體才能執行著色器程式碼。 特定種類的著色器 (其由 [著色器類型] 屬性指定) 僅可用於較新的著色器模型；例如，在著色器模型 5 中引入了計算著色器。

   此屬性對應於 HLSL 編譯器的 **/T \[type]_\[model]** 命令列引數的 **\[model]** 部分。 [著色器類型] 屬性則會指定引數的 **[type]** 部分。

- **前置處理器定義**

   新增一或多個要套用至 HLSL 原始程式碼檔案的前置處理器符號定義。 請使用分號來分隔這些符號定義。

   此屬性對應於 HLSL 編譯器的 **/D \[definitions]** 命令列引數。

## <a name="see-also"></a>另請參閱

[HLSL 屬性頁](hlsl-property-pages.md)<br>
[HLSL 屬性頁：進階](hlsl-property-pages-advanced.md)<br>
[HLSL 屬性頁：輸出檔案](hlsl-property-pages-output-files.md)
