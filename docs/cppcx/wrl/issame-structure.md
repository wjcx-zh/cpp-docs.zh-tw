---
title: IsSame 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
- internal/Microsoft::WRL::Details::IsSame::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsSame structure
- Microsoft::WRL::Details::IsSame::value constant
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
ms.openlocfilehash: b659f832756b79289181db34fa8d6fc0d974609d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161273"
---
# <a name="issame-structure"></a>IsSame 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename T1, typename T2>
struct IsSame;

template <typename T1>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>參數

*T1*<br/>
類型。

*T2*<br/>
另一個型別。

## <a name="remarks"></a>備註

其中一個指定的型別是否相當於另一個測試指定的類型。

## <a name="members"></a>成員

### <a name="public-constants"></a>公用常數

名稱                    | 描述
----------------------- | --------------------------------------------------
[IsSame::value](#value) | 表示一種型別是否與另一個相同。

## <a name="inheritance-hierarchy"></a>繼承階層

`IsSame`

## <a name="requirements"></a>需求

**標頭：** internal.h

**命名空間：** Microsoft::WRL::Details

## <a name="value"></a>Issame:: Value

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
template <typename T1, typename T2>
struct IsSame
{
    static const bool value = false;
};

template <typename T1>
struct IsSame<T1, T1>
{
    static const bool value = true;
};
```

### <a name="remarks"></a>備註

表示一種型別是否與另一個相同。

`value` 是 **，則為 true**如果範本參數相同，並**false**範本參數是否不同。
