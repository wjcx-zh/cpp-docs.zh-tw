---
title: pointers_to_members pragma
ms.date: 08/29/2019
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
ms.openlocfilehash: fb5b277252b6c1422a87c5f2a2e2b7230ec49632
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219069"
---
# <a name="pointers_to_members-pragma"></a>pointers_to_members pragma

**C++特殊**

指定類別成員的指標是否可以在其相關聯的類別定義之前宣告。 用來控制指標大小, 以及解讀指標所需的程式碼。

## <a name="syntax"></a>語法

> **#pragma pointers_to_members (** *指標*宣告 [ **,** *最常見的表示*])

## <a name="remarks"></a>備註

您可以將**pointers_to_members** pragma 放在原始程式檔中, 做為使用[/vmb 或/vmg](../build/reference/vmb-vmg-representation-method.md)編譯器選項或[繼承關鍵字](../cpp/inheritance-keywords.md)的替代方法。

*指標*宣告引數會指定您是否已在相關聯函式定義之前或之後宣告成員的指標。 *指標*宣告引數是下列兩個符號之一:

| 引數 | 註解 |
|--------------|--------------|
| **full_generality** | 產生安全但有時並非是最佳化的程式碼。 如果成員的任何指標在相關聯的類別定義之前宣告, 您會使用**full_generality** 。 這個引數一律會使用*最常見的標記法*引數所指定的指標標記法。 等於 /vmg。 |
| **best_case** | 使用所有成員指標的 best-case 表示，產生安全且最佳化的程式碼。 需要在宣告類別成員的指標之前先定義類別。 預設值為**best_case**。 |

*最常見的標記法*引數會指定最小的指標標記法, 讓編譯器可以安全地用來參考轉譯單位中類別成員的任何指標。 引數可以是下列其中一個值:

| 引數 | 註解 |
|--------------|--------------|
| **single_inheritance** | 最常見的表示是單一繼承的成員函式指標。 如果宣告其成員指標類別定義的繼承模型為多重或虛擬，則會產生錯誤。 |
| **multiple_inheritance** | 最常見的表示是多重繼承的成員函式指標。 如果宣告其成員指標類別定義的繼承模型為虛擬，則會產生錯誤。 |
| **virtual_inheritance** | 最常見的表示是虛擬繼承的成員函式指標。 永遠不會產生錯誤。 當使用時`#pragma pointers_to_members(full_generality)` , virtual_inheritance 是預設引數。 |

> [!CAUTION]
> 我們建議您只將**pointers_to_members** pragma 放在您想要影響的原始程式碼檔案中, 而且只有在任何`#include`指示詞之後。 這種作法可使 pragma 影響到其他檔案的風險降低，否則，您會意外地為相同的變數、函式或類別名稱指定多個定義。

## <a name="example"></a>範例

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**結束C++特定**

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
