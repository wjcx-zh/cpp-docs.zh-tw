---
title: optimize pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 6d7b99b7a72c133d56a209cf42fa9ef670a4a7f9
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220511"
---
# <a name="optimize-pragma"></a>optimize pragma

依函式指定每個函數的優化。

## <a name="syntax"></a>語法

> **#pragma optimize ("** [*優化-list* ] **",** { **on**  |  **off** } **)**

## <a name="remarks"></a>備註

**Optimize** pragma 必須出現在函式外部。 它會在出現 pragma 之後定義的第一個函式生效。 **On**和**off**引數會開啟或關閉*優化清單*中指定的選項。

*優化清單*可以是下表所示的零個或多個參數。

### <a name="parameters-of-the-optimize-pragma"></a>最佳化 Pragma 的參數

| 參數 | 最佳化類型 |
|--------------------|--------------------------|
| **g** | 啟用全域最佳化。 |
| **s**或**t** | 指定機器碼的短 (short) 序列或快速 (fast) 序列。 |
| **y** | 在程式堆疊上產生框架指標。 |

這些參數與[/o](../build/reference/o-options-optimize-code.md)編譯器選項所使用的字母相同。 例如，下列 pragma 相當於 `/Os` 編譯器選項：

```cpp
#pragma optimize( "s", on )
```

使用**optimize** pragma 搭配空字串 ( **""** ) 是特殊形式的指示詞:

當您使用**off**參數時, 它會將所有優化、 **g**、 **s**、 **t**和**y**關閉。

當您使用**on**參數時, 它會將優化重設為您使用[/o](../build/reference/o-options-optimize-code.md)編譯器選項指定的優化。

```cpp
#pragma optimize( "", off )
/* unoptimized code section */
#pragma optimize( "", on )
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
