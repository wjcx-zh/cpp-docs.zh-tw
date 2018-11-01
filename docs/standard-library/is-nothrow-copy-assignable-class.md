---
title: is_nothrow_copy_assignable 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
ms.openlocfilehash: bb3aca47b61bdcc5b28eeedc1a6b4edefc303c4e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583750"
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable 類別

測試類型是否具有編譯器已知不會擲回的複製指派運算子。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>參數

*T*<br/>
要查詢的類型。

## <a name="remarks"></a>備註

類型述詞的執行個體亦適用於可參考的型別*T*其中`is_nothrow_assignable<T&, const T&>`保存 true; 否則為 false。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_nothrow_assignable 類別](../standard-library/is-nothrow-assignable-class.md)<br/>
