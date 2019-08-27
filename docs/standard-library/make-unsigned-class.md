---
title: make_unsigned 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_unsigned
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
ms.openlocfilehash: 4c0224bd5fd7dc8c6589ae474bb9acb9a8f09cf6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456317"
---
# <a name="makeunsigned-class"></a>make_unsigned 類別

建立類型，或是建立大於或等於類型大小的最小無正負號類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*T*|要修改的類型。|

## <a name="remarks"></a>備註

如果`is_unsigned<T>`保留 true, 則類型修飾詞的實例會保留已修改的類型, 也就是*T* 。 否則是最小的帶正負號類型 `ST`，其中 `sizeof (T) <= sizeof (ST)`。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
