---
title: stdext 命名空間 | Microsoft Docs
ms.custom: ''
ms.date: 09/06/2017
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stdext
dev_langs:
- C++
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 302d5b696a3413e36dd76cb931556a3fae7e7615
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859195"
---
# <a name="stdext-namespace"></a>stdext 命名空間

成員[ \<hash_map >](../standard-library/hash-map.md)和[ \<hash_set >](../standard-library/hash-set.md)標頭檔目前不是 ISO c + + 標準的一部分。 因此，這些類型和成員已從 `std` 命名空間移至 `stdext`命名空間，以持續符合 C++ 標準。

編譯時[/Ze](../build/reference/za-ze-disable-language-extensions.md)，這是預設值，編譯器會發出警告，於使用`std`之成員的\<hash_map > 和\<hash_set > 標頭檔。 若要停用警告，請使用 [warning](../preprocessor/warning.md) pragma。

若要讓編譯器產生錯誤，而使用`std`之成員的\<hash_map > 和\<hash_set > 標頭檔與 **/Ze**，加入下列指示詞，才能`#include`任何 c + + 標準程式庫標頭檔。

```cpp
#define _DEFINE_DEPRECATED_HASH_CLASSES 0
```

編譯時 **/Za**，編譯器會產生錯誤。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)

