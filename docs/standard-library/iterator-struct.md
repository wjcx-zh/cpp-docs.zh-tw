---
title: iterator 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::iterator
dev_langs:
- C++
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9cd414e2e6f23cb2fe44e6de4b5f53b33ef3555
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857879"
---
# <a name="iterator-struct"></a>iterator 結構

空的基底結構，用來確保使用者定義的迭代器類別能夠與 **iterator_trait** 正常搭配運作。

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

- `value_type` (與範本參數 **Type** 同義)。

- `difference_type` (與範本參數 `Distance` 同義)。

- `distance_type` (與範本參數 `Distance` 同義)

- `pointer` (與範本參數 `Pointer` 同義)。

- `reference` (與範本參數 `Reference` 同義)。

請注意，`value_type` 不應該是常數類型，即使 **pointer** 指向 const **Type** 的物件且參考指定的物件是 const **Type** 亦同。

## <a name="example"></a>範例

如需如何在迭代器基底類別中宣告及使用類型的範例，請參閱 [iterator_traits](../standard-library/iterator-traits-struct.md)。

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
