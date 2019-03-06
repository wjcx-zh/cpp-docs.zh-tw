---
title: /Og (全域最佳化)
ms.date: 09/22/2017
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
ms.openlocfilehash: e8032d7dbd771ca1527c6515a779b0f532a2c658
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420865"
---
# <a name="og-global-optimizations"></a>/Og (全域最佳化)

已取代。 提供本機和全域最佳化自動暫存器配置，以及迴圈最佳化。 我們建議您改用其中一個[/o1 （最小大小）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)或是[/o2 （最快速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)改。

## <a name="syntax"></a>語法

> /Og

## <a name="remarks"></a>備註

**/Og**已被取代。 這些最佳化現在通常預設會啟用。 如需有關最佳化的詳細資訊，請參閱 < [/o1，/o2 （最小大小、 最快速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)或是[/Ox （啟用最速度最佳化）](../../build/reference/ox-full-optimization.md)。

下列最佳化會位於 **/Og**:

- 本機和全域通用子運算式刪除

   在這種最佳化通用子運算式的值會計算一次。 在下列範例中，如果的值`b`及`c`不會變更的三個運算式之間，編譯器可以將計算指派`b + c`給暫存變數，並取代為變數`b + c`:

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   對於本機的通用子運算式最佳化，編譯器會檢查簡短的通用子運算式的程式碼區段。 對於全域通用子運算式最佳化，編譯器會搜尋整個函式中的通用子運算式。

- 自動暫存器配置

   此最佳化會讓編譯器將儲存經常使用變數和子運算式在暫存器;`register`關鍵字會被忽略。

- 迴圈最佳化

   此最佳化會移除在迴圈主體中的非變異的子運算式。 最佳的迴圈包含其值會隨著每次執行迴圈的運算式。 在下列範例中，運算式`x + y`迴圈主體中不會變更：

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

   在最佳化之後，`x + y`計算一次而不是每次執行迴圈：

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

   編譯器會假設沒有別名，您使用設定時，迴圈最佳化會更有效[__restrict](../../cpp/extension-restrict.md)， [noalias](../../cpp/noalias.md)，或[限制](../../cpp/restrict.md)。

   > [!NOTE]
   > 您可以啟用或停用根據函式的函式使用的全域最佳化`optimize`pragma 搭配`g`選項。

如需相關資訊，請參閱[/Oi （產生內建函式）](../../build/reference/oi-generate-intrinsic-functions.md)並[/Ox （啟用最速度最佳化）](../../build/reference/ox-full-optimization.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 輸入中的編譯器選項**其他選項** 方塊中。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/O 選項 (最佳化程式碼)](../../build/reference/o-options-optimize-code.md)

[編譯器選項](../../build/reference/compiler-options.md)

[設定編譯器選項](../../build/reference/setting-compiler-options.md)
