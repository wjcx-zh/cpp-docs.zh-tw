---
title: '&lt;sstream&gt; 函式 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- sstream/std::swap
ms.assetid: bc9607e8-7c6b-44ef-949b-19e917b450ad
ms.openlocfilehash: 354632a3c001f2352821d9a1d0b493291c21a337
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953933"
---
# <a name="ltsstreamgt-functions"></a>&lt;sstream&gt; 函式

||
|-|
|[swap](#sstream_swap)|

## <a name="sstream_swap"></a> swap

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
|*left*|`sstream` 物件的參考。|
|*right*|`sstream` 物件的參考。|

### <a name="remarks"></a>備註

這個範本函式會執行 `left.swap(right)`。

## <a name="see-also"></a>另請參閱

[\<sstream>](../standard-library/sstream.md)<br/>
