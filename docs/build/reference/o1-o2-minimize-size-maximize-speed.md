---
title: /O1、/O2 (最小大小、最快速度)
description: MSVC 編譯器選項/O1 和/O2 會指定最小大小或最大速度的所有優化。
ms.date: 07/08/2020
f1_keywords:
- /O2
- /O1
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
ms.openlocfilehash: c1eda8395e604468cbb23572ec930d6171984fe4
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180899"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>`/O1`， `/O2` (大小，最大化速度) 

選取一組預先定義的選項，其會影響所產生程式碼的大小和速度。

## <a name="syntax"></a>語法

> **`/O1`**\
> **`/O2`**

## <a name="remarks"></a>備註

**`/O1`** 和 **`/O2`** 編譯器選項可讓您快速地一次設定數個特定的優化選項。 **`/O1`** 選項會設定在大部分案例中建立最小程式代碼的個別優化選項。 **`/O2`** 選項會設定在大部分案例中建立最快速程式碼的選項。 **`/O2`** 選項是 [發行組建] 的預設值。 下表顯示由和所設定的特定選項 **`/O1`** **`/O2`** ：

| 選項 | 相當於 |
|--|--|
| **`/O1`** (大小降)  | [`/Og`](og-global-optimizations.md) [`/Os`](os-ot-favor-small-code-favor-fast-code.md) [`/Oy`](oy-frame-pointer-omission.md) [`/Ob2`](ob-inline-function-expansion.md) [`/GF`](gf-eliminate-duplicate-strings.md) [`/Gy`](gy-enable-function-level-linking.md) |
| **`/O2`** (最大化速度)  | [`/Og`](og-global-optimizations.md) [`/Oi`](oi-generate-intrinsic-functions.md) [`/Ot`](os-ot-favor-small-code-favor-fast-code.md) [`/Oy`](oy-frame-pointer-omission.md) [`/Ob2`](ob-inline-function-expansion.md) [`/GF`](gf-eliminate-duplicate-strings.md) [`/Gy`](gy-enable-function-level-linking.md) |

**`/O1`** 和 **`/O2`** 是互斥的。

> [!NOTE]
> **x86 特定**\
> 這些選項表示使用框架指標省略 ([`/Oy`](oy-frame-pointer-omission.md)) 選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **優化**] 屬性頁。

1. 修改**優化**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A> ＞。

## <a name="see-also"></a>另請參閱

[`/O` (優化程式碼的選項) ](o-options-optimize-code.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[`/EH` (例外狀況處理模型) ](eh-exception-handling-model.md)
