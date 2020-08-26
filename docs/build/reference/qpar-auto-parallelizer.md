---
title: /Qpar (自動平行化工具)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
ms.openlocfilehash: effe1ad7799022ea85184513de1dc48c72d6bfcb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839435"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (自動平行化工具)

啟用編譯器的 [自動平行化工具](../../parallel/auto-parallelization-and-auto-vectorization.md) 功能，在您的程式碼中自動平行化迴圈。

## <a name="syntax"></a>語法

```
/Qpar
```

## <a name="remarks"></a>備註

當編譯器自動平行化程式碼中的迴圈時，它會將計算分散到多個處理器核心。 只有在編譯器判斷這是合法的做法，且平行處理會改善效能時，才會進行迴圈平行化。

`#pragma loop()` 指示詞可以協助最佳化平行處理特定的迴圈。 如需詳細資訊，請參閱 [迴圈](../../preprocessor/loop.md)。

如需有關如何啟用自動平行化工具輸出訊息的詳細資訊，請參閱 [/Qpar-report (自動平行化工具報告層級) ](qpar-report-auto-parallelizer-reporting-level.md)。

### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定 /Qpar 編譯器選項

1. 在 **方案總管**中，開啟專案的快捷方式功能表，然後選擇 [ **屬性**]。

1. 在 [ **屬性頁** ] 對話方塊的 [ **C/c + +**] 底下，選取 [ **命令列**]。

1. 在 [ **其他選項** ] 方塊中，輸入 `/Qpar` 。

### <a name="to-set-the-qpar-compiler-option-programmatically"></a>若要以程式設計方式設定 /Qpar 編譯器選項

- 請使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的範例程式碼。

## <a name="see-also"></a>另請參閱

[ (低層級作業的/q 選項) ](q-options-low-level-operations.md)<br/>
[/Qpar-report (自動平行化工具報告層級) ](qpar-report-auto-parallelizer-reporting-level.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[#pragma 迴圈 ( # B1 ](../../preprocessor/loop.md)<br/>
[Visual Studio 中的機器碼向量化](/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
