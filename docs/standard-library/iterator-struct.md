---
title: iterator 結構
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: b45cdb5c3d4608296cca34ad6a0be6e25b588d28
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222299"
---
# <a name="iterator-struct"></a>iterator 結構

空的基底結構，用來確保使用者定義的反覆運算器類別可與一起正常運作 `iterator_trait` 。

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

請注意， `value_type` 即使 `pointer` 在的物件和 reference 中的點 **`const`** `Type` 指定了的物件， **`const`** 也不應該是常數型別 `Type` 。

## <a name="example"></a>範例

如需如何在迭代器基底類別中宣告及使用類型的範例，請參閱 [iterator_traits](../standard-library/iterator-traits-struct.md)。

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<iterator>](../standard-library/iterator.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
