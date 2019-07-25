---
title: make_signed 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_signed
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
ms.openlocfilehash: c3c35e28dec3270299329c0186273e324effc2bb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453675"
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

*而已*\
要修改的類型。

## <a name="remarks"></a>備註

如果`is_signed<T>`保留 true, 則類型修飾詞的實例會保留已修改的類型, 也就是*T* 。 否則，是最小的未帶正負號類型 `UT`，其中 `sizeof (T) <= sizeof (UT)`。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
