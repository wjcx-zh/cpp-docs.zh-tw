---
title: -Qpar （自動平行化工具） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
dev_langs:
- C++
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a701183becc7a561ca778dea383fdb57181d8da4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710771"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (自動平行化工具)

可讓[Auto-parallelizer](../../parallel/auto-parallelization-and-auto-vectorization.md)編譯器自動平行化迴圈程式碼中的功能。

## <a name="syntax"></a>語法

```
/Qpar
```

## <a name="remarks"></a>備註

當編譯器自動平行化程式碼中的迴圈時，它會將計算分散到多個處理器核心。 只有在編譯器判斷這是合法的做法，且平行處理會改善效能時，才會進行迴圈平行化。

`#pragma loop()` 指示詞可以協助最佳化平行處理特定的迴圈。 如需詳細資訊，請參閱 <<c0> [ 迴圈](../../preprocessor/loop.md)。

如需如何啟用 auto-parallelizer 輸出訊息的詳細資訊，請參閱[/Qpar-report （自動平行化工具報告層級）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)。

### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定 /Qpar 編譯器選項

1. 在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **屬性**]。

1. 在 **屬性頁**對話方塊的  **C/c + +**，選取**命令列**。

1. 在 **其他選項**方塊中，輸入`/Qpar`。

### <a name="to-set-the-qpar-compiler-option-programmatically"></a>若要以程式設計方式設定 /Qpar 編譯器選項

- 請使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的範例程式碼。

## <a name="see-also"></a>另請參閱

[/Q 選項 （低階運算）](../../build/reference/q-options-low-level-operations.md)
[/Qpar-report （自動平行化工具報告層級）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[#pragma loop （)](../../preprocessor/loop.md)
[原生程式碼的平行程式設計](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)