---
title: "-Og （全域最佳化） |Microsoft 文件"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
dev_langs: C++
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 196e89a958ce49bf5e0087d98d2f40ada210cc87
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="og-global-optimizations"></a>/Og (全域最佳化)

已取代。 提供本機和全域最佳化自動暫存器配置，以及迴圈最佳化。 我們建議您可使用[/O1 （最小化大小）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)或[/O2 （最大化的速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)改為。

## <a name="syntax"></a>語法

> /Og

## <a name="remarks"></a>備註

**/Og**已被取代。 現在根據預設通常啟用這些最佳化。 如需有關最佳化的詳細資訊，請參閱[/O1、 /O2 （最小化的大小、 最大化的速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)或[/Ox （啟用最速度最佳化）](../../build/reference/ox-full-optimization.md)。

下列最佳化底下可用**/Og**:

- 本機和全域通用子運算式刪除

     在這種最佳化通用子運算式的值會計算一次。 在下列範例中，如果值`b`和`c`不會變更的三個運算式之間，編譯器可以將計算指派`b + c`到暫存變數，並以取代變數`b + c`:

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

     對於本機的通用子運算式最佳化，編譯器會檢查簡短的通用子運算式的程式碼區段。 對於全域通用子運算式最佳化，編譯器會搜尋整個函式的通用子運算式。

- 自動暫存器配置

     此最佳化可讓編譯器在儲存經常使用變數和子運算式在暫存器。`register`關鍵字會被忽略。

- 迴圈最佳化

     此最佳化會移除在迴圈主體中而異的子運算式。 最佳的迴圈包含的值會隨著每次執行迴圈的運算式。 在下列範例中，運算式`x + y`迴圈主體中不會變更：

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

     迴圈最佳化編譯器可以假設沒有別名，您會更有效[__restrict](../../cpp/extension-restrict.md)， [noalias](../../cpp/noalias.md)，或[限制](../../cpp/restrict.md)。

    > [!NOTE]
    > 您可以啟用或停用函式的函式使用全域最佳化`optimize`pragma 搭配`g`選項。

 如需相關資訊，請參閱[/Oi （產生內建函式）](../../build/reference/oi-generate-intrinsic-functions.md)和[/Ox （啟用最速度最佳化）](../../build/reference/ox-full-optimization.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 輸入中的編譯器選項**其他選項**方塊。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>請參閱

[/O 選項 （最佳化程式碼）](../../build/reference/o-options-optimize-code.md)

[編譯器選項](../../build/reference/compiler-options.md)

[設定編譯器選項](../../build/reference/setting-compiler-options.md)