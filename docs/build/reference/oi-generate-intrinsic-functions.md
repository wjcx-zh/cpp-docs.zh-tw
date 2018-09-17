---
title: -Oi （產生內建函式） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
dev_langs:
- C++
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 527f326d629bc8d41efcd73a938994570bed4d2e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725914"
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi (產生內建函式)

取代某些函式呼叫，以協助您的應用程式內建函式或其他特殊形式的函式的執行速度。

## <a name="syntax"></a>語法

```
/Oi[-]
```

## <a name="remarks"></a>備註

使用內建函式的程式是更快，因為它們不需要的函式呼叫額外負荷，但可能是因為建立額外的程式碼更大。

請參閱[內建](../../preprocessor/intrinsic.md)如有內建形式之函式的詳細資訊。

**/Oi**只是要求編譯器內建函式，以取代某些函式呼叫，編譯器可能會呼叫函式 （和取代函式呼叫內建） 如果會產生較佳的效能。

**x86 特定**

內建函式的浮點函式不執行任何特殊的檢查輸入值並因此用於限制範圍的輸入，且不同的例外狀況處理與具有相同名稱的程式庫常式比界限條件。 使用真正的內建形式表示遺失的 IEEE 例外狀況處理，而失去`_matherr`和`errno`功能; 後者表示遺失的 ANSI 合規性。 不過，這些內建形式可以顯著地加快浮點密集的程式，且對於許多程式，一致性問題有一些實用的值。

您可以使用[Za](../../build/reference/za-ze-disable-language-extensions.md)覆寫產生真正的內建浮點選項的編譯器選項。 在這種情況下，函式會產生為程式庫常式，將引數直接傳遞至浮點晶片，而不是將引數推送至程式堆疊。

**結束 x86 特定**

您也使用[內建函式](../../preprocessor/intrinsic.md)若要建立內建函式，或是[函式 （C/c + +）](../../preprocessor/function-c-cpp.md)明確強制執行函式呼叫。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **最佳化**屬性頁。

1. 修改**啟用內建函式**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>。

## <a name="see-also"></a>另請參閱

[/O 選項 （最佳化程式碼）](../../build/reference/o-options-optimize-code.md)
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[編譯器內建](../../intrinsics/compiler-intrinsics.md)