---
title: /Og (全域最佳化)
description: 描述已被取代的 MSVC 編譯器選項/Og，先前用來啟用全域優化。
ms.date: 07/08/2020
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
ms.openlocfilehash: c1cab53ccb391bd7d6ca7660e2750f53aa7c72e4
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180847"
---
# <a name="og-global-optimizations"></a>`/Og` (全域優化) 

已被取代。 提供本機和全域優化、自動註冊配置和迴圈優化。 建議您改用 (將[ `/O1` 大小降至最低) ](o1-o2-minimize-size-maximize-speed.md)或[ `/O2` (最大化速度) ](o1-o2-minimize-size-maximize-speed.md) 。

## <a name="syntax"></a>語法

> **`/Og`**

## <a name="remarks"></a>備註

**`/Og`** 已被取代。 當啟用任何優化時，現在預設會啟用這些優化。 如需優化的詳細資訊，請參閱[ `/O1` `/O2` (最小化大小、最大化速度) ](o1-o2-minimize-size-maximize-speed.md)或[ `/Ox` (啟用大部分速度優化) ](ox-full-optimization.md)。

下列是可用的優化功能 **`/Og`** ：

- 本機和全域通用子運算式刪除

   在此優化中，會計算通用子運算式的值一次。 在下列範例中，如果和的值 `b` `c` 不會在三個運算式之間變更，則編譯器可以將的計算指派 `b + c` 給暫存變數，並使用該變數來進行 `b + c` 下列動作：

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   針對本機通用子運算式優化，編譯器會針對通用子運算式檢查程式碼的簡短區段。 對於全域通用子運算式優化，編譯器會搜尋整個函式中的通用子運算式。

- 自動註冊配置

   這項優化可讓編譯器在暫存器中儲存經常使用的變數和子運算式;`register`已忽略關鍵字。

- 迴圈優化

   這項優化會從迴圈的主體移除不變的子運算式。 最佳迴圈僅包含其值會在每次執行迴圈時變更的運算式。 在下列範例中，運算式 `x + y` 不會在迴圈主體中變更：

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

   優化之後， `x + y` 會計算一次，而不是每次執行迴圈時：

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

   當編譯器可以假設沒有任何別名（您使用、或來設定）時，迴圈優化會更有效率 [`__restrict`](../../cpp/extension-restrict.md) [`noalias`](../../cpp/noalias.md) [`restrict`](../../cpp/restrict.md) 。

   > [!NOTE]
   > 您可以使用 pragma 搭配選項，逐一啟用或停用每個函式的全域優化功能 `optimize` `g` 。

如需相關資訊，請參閱[ `/Oi` (產生內建函式) ](oi-generate-intrinsic-functions.md)和[ `/Ox ` (啟用最快速優化) ](ox-full-optimization.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
