---
title: '&lt;sstream&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- sstream/std::swap
ms.assetid: bc9607e8-7c6b-44ef-949b-19e917b450ad
ms.openlocfilehash: bdf7cd26b25680eb7e5270fdc8ae7dac0d10f70f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336646"
---
# <a name="ltsstreamgt-functions"></a>&lt;sstream&gt; 函式

||
|-|
|[交換](#sstream_swap)|

## <a name="swap"></a><a name="sstream_swap"></a>交換

在 `sstream` 物件之間交換值。

```cpp
template <class Elem, class Tr, class Alloc>
void swap(
    basic_stringbuf<Elem, Tr, Alloc>& left,
    basic_stringbuf<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_istringstream<Elem, Tr, Alloc>& left,
    basic_istringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_ostringstream<Elem, Tr, Alloc>& left,
    basic_ostringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_stringstream<Elem, Tr, Alloc>& left,
    basic_stringstream<Elem, Tr, Alloc>& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*離開*|`sstream` 物件的參考。|
|*對*|`sstream` 物件的參考。|

### <a name="remarks"></a>備註

這個範本函式會執行 `left.swap(right)`。

## <a name="see-also"></a>另請參閱

[\<溪流>](../standard-library/sstream.md)
