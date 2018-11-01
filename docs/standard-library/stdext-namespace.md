---
title: stdext 命名空間
ms.date: 09/06/2017
f1_keywords:
- stdext
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
ms.openlocfilehash: aeba486393e6b45481108f967f3de8eb73a0adea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468480"
---
# <a name="stdext-namespace"></a>stdext 命名空間

成員[ \<hash_map >](../standard-library/hash-map.md)並[ \<hash_set >](../standard-library/hash-set.md)標頭檔目前不是 ISO c + + 標準的一部分。 因此，這些類型和成員已從 `std` 命名空間移至 `stdext`命名空間，以持續符合 C++ 標準。

進行編譯時[/Ze](../build/reference/za-ze-disable-language-extensions.md)，這是預設值，編譯器會發出警告，在使用`std`的成員\<hash_map > 和\<hash_set > 標頭檔。 若要停用警告，請使用 [warning](../preprocessor/warning.md) pragma。

若要讓編譯器產生的錯誤`std`的成員\<hash_map > 和\<hash_set > 標頭檔與 **/Ze**，新增下列指示詞之前`#include`任何 c + + 標準程式庫標頭檔。

```cpp
#define _DEFINE_DEPRECATED_HASH_CLASSES 0
```

進行編譯時 **/Za**，編譯器會產生錯誤。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)

