---
title: nullopt_t 結構
ms.date: 08/04/2019
f1_keywords:
- optional/std::nullopt_t
- optional/std::nullopt
ms.openlocfilehash: 1f453a5d75de3f6dedb133d55c094a4f4274e08f
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957050"
---
# <a name="nullopt_t-struct"></a>nullopt_t 結構

類型是唯一的空白類型, 用來表示[選擇性](optional-class.md)的物件不包含值。`nullopt_t`

類型`nullopt` `optional`的常數表示類型具有未初始化的狀態。 `nullopt_t` 它可以用來初始化`optional`物件或與之比較。

## <a name="syntax"></a>語法

```cpp
struct nullopt_t;
inline constexpr nullopt_t nullopt{ /*implementation-defined*/ };
```

## <a name="see-also"></a>另請參閱

[\<選擇性 >](optional.md)\
[選擇性類別](optional-class.md)
