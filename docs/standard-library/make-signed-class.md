---
title: make_signed 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_signed
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
ms.openlocfilehash: c9fe9d54d503f1aa1dfb3debfaeb7649f2e5c18d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631643"
---
# <a name="makesigned-class"></a>make_signed 類別

建立類型，或是建立大於或等於類型大小的最小帶正負號類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct make_signed;

template <class T>
using make_signed_t = typename make_signed<T>::type;
```

### <a name="parameters"></a>參數

*T*<br/>
要修改的類型。

## <a name="remarks"></a>備註

類型修飾詞的執行個體保留修改的類型所*T*如果`is_signed<T>`保存，則為 true。 否則，是最小的未帶正負號類型 `UT`，其中 `sizeof (T) <= sizeof (UT)`。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
