---
title: make_unsigned 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_unsigned
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
ms.openlocfilehash: 42c722c5250a4989b930d8f1e6fe52f2eccc614a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413043"
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

類型修飾詞的執行個體保留修改的類型所*T*如果`is_unsigned<T>`保存，則為 true。 否則是最小的帶正負號類型 `ST`，其中 `sizeof (T) <= sizeof (ST)`。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
