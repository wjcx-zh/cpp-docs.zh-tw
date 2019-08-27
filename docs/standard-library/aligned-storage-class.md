---
title: aligned_storage 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_storage
helpviewer_keywords:
- aligned_storage class
- aligned_storage
ms.assetid: f255e345-1f05-4d07-81e4-017f420839fb
ms.openlocfilehash: 8a4e907faa6175b9e03f5367d09501aaea388bce
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456470"
---
# <a name="alignedstorage-class"></a>aligned_storage 類別

建立適當對齊的類型。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Len, std::size_t Align>
struct aligned_storage;

template <std::size_t Len, std::size_t Align = alignment_of<max_align_t>::value>
using aligned_storage_t = typename aligned_storage<Len, Align>::type;
```

### <a name="parameters"></a>參數

*Len*\
物件大小。

*對齊*\
物件對齊。

## <a name="remarks"></a>備註

範本成員 typedef `type`是具有對齊和大小*Len*之 POD 類型的同義字。 某些`alignment_of<T>::value` 類型`T`的對齊必須等於, 或預設的對齊方式。

## <a name="example"></a>範例

```cpp
#include <type_traits>
#include <iostream>

typedef std::aligned_storage<sizeof (int),
    std::alignment_of<double>::value>::type New_type;
int main()
    {
    std::cout << "alignment_of<int> == "
        << std::alignment_of<int>::value << std::endl;
    std::cout << "aligned to double == "
        << std::alignment_of<New_type>::value << std::endl;

    return (0);
    }
```

```Output
alignment_of<int> == 4
aligned to double == 8
```

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[alignment_of 類別](../standard-library/alignment-of-class.md)
