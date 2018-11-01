---
title: iterator 結構
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: 1dd62a6141e690d3bd4dcad69aa107c126a0f386
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631396"
---
# <a name="iterator-struct"></a>iterator 結構

空的基底結構，用來確保使用者定義的迭代器類別能夠適當運作與`iterator_trait`s。

## <a name="syntax"></a>語法

```cpp
struct iterator {
   typedef Category iterator_category;
   typedef Type value_type;
   typedef Distance difference_type;
   typedef Distance distance_type;
   typedef Pointer pointer;
   typedef Reference reference;
   };
```

## <a name="remarks"></a>備註

此範本結構可作為所有迭代器的基底類型。 它會定義成員類型

- `iterator_category` (與範本參數 `Category` 同義)。

- `value_type` (與範本參數 `Type` 同義)。

- `difference_type` (與範本參數 `Distance` 同義)。

- `distance_type` (與範本參數 `Distance` 同義)

- `pointer` (與範本參數 `Pointer` 同義)。

- `reference` (與範本參數 `Reference` 同義)。

請注意，`value_type`不應該是常數的類型，即使`pointer`指向的物件**const** `Type`且參考指定的物件**const** `Type`。

## <a name="example"></a>範例

如需如何在迭代器基底類別中宣告及使用類型的範例，請參閱 [iterator_traits](../standard-library/iterator-traits-struct.md)。

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
