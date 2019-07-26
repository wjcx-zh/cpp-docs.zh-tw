---
title: '&lt;typeindex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <typeindex>
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
ms.openlocfilehash: 237356a0862ec3fc591264b482b23e62ef2c51cb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455054"
---
# <a name="lttypeindexgt"></a>&lt;typeindex&gt;

包含標準標頭 \<typeindex> 以定義支援對類別 [type_info](../cpp/type-info-class.md) 之物件編製索引的類別與函式。

## <a name="syntax"></a>語法

```cpp
#include <typeindex>
```

## <a name="remarks"></a>備註

[Hash 結構](../standard-library/hash-structure.md)定義適合用來將類型 [type_index](../standard-library/type-index-class.md) 的值對應到索引值散佈的 `hash function`。

`type_index` 類別會將指標包裝到 `type_info` 物件來協助編製索引。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
