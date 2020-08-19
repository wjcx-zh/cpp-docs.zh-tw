---
title: make_unsigned 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_unsigned
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
ms.openlocfilehash: 46b785b20d2ca8ff2de0dfa678b543fa7493aa92
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561748"
---
# <a name="make_unsigned-class"></a>make_unsigned 類別

建立類型，或是建立大於或等於類型大小的最小無正負號類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```

### <a name="parameters"></a>參數

*10gbase-t*\
要修改的類型。

## <a name="remarks"></a>備註

型別修飾詞的實例會保存修改的類型，如果保留 true，就會是 *T* `is_unsigned<T>` 。 否則是最小的帶正負號類型 `ST`，其中 `sizeof (T) <= sizeof (ST)`。

## <a name="requirements"></a>規格需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
