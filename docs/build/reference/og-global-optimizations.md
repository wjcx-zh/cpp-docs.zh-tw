---
title: /Og (全域最佳化)
description: 描述已淘汰的 MSVC 編譯器選項/Og，先前用來啟用全域優化。
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
ms.openlocfilehash: 2d5baf4967f4f4f945540d2a7baef399974d2d42
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506579"
---
# <a name="og-global-optimizations"></a>`/Og` (全域優化) 

已取代。 提供本機和全域優化、自動註冊配置和迴圈優化。 建議您改為使用[ `/O1` (將大小降至最低) ](o1-o2-minimize-size-maximize-speed.md)或[ `/O2` () 最快速度](o1-o2-minimize-size-maximize-speed.md)。

## <a name="syntax"></a>語法

> **`/Og`**

## <a name="remarks"></a>備註

**`/Og`** 已淘汰。 當啟用任何優化時，現在預設會啟用這些優化。 如需優化的詳細資訊，請參閱[ `/O1` `/O2` (將大小最小化、最大化速度) ](o1-o2-minimize-size-maximize-speed.md)，或[ `/Ox` (啟用最快速的優化) ](ox-full-optimization.md)。

以下是可用的優化 **`/Og`** ：

- 本機和全域通用子運算式刪除

   在這項優化中，通用子運算式的值會計算一次。 在下列範例中，如果 `b` 和 `c` 這三個運算式之間的值不會變更，則編譯器可以將的計算指派 `b + c` 給暫存變數，並將該變數用於 `b + c` ：

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   針對本機通用子運算式優化，編譯器會檢查常用子運算式的簡短程式碼區段。 針對全域通用子運算式優化，編譯器會搜尋一般子運算式的整個函數。

- 自動註冊配置

   這項優化可讓編譯器將常用的變數和子運算式儲存在暫存器中; **`register`** 已忽略關鍵字。

- 迴圈優化

   這項優化會從迴圈主體移除不變的子運算式。 最佳迴圈只包含值會在每次執行迴圈時變更的運算式。 在下列範例中，運算式 `x + y` 不會在迴圈主體中變更：

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

   經過優化之後， `x + y` 會計算一次，而不是每次執行迴圈時：

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

   當編譯器無法假設您使用、或所設定的別名時，迴圈優化會更 [`__restrict`](../../cpp/extension-restrict.md) 有效率 [`noalias`](../../cpp/noalias.md) [`restrict`](../../cpp/restrict.md) 。

   > [!NOTE]
   > 您可以 `optimize` 搭配使用 pragma 與選項，來啟用或停用每個函式的全域優化 `g` 。

如需相關資訊，請參閱[ `/Oi` (產生內建函式) ](oi-generate-intrinsic-functions.md)和[ `/Ox` (啟用最快速的優化) ](ox-full-optimization.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **命令列**] 屬性頁。

1. 在 [ **其他選項** ] 方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
