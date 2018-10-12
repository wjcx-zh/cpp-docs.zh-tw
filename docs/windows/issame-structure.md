---
title: IsSame 結構 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
- internal/Microsoft::WRL::Details::IsSame::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::IsSame structure
- Microsoft::WRL::Details::IsSame::value constant
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2af59860016835f8e8dfddc9d0a77204ff866bd3
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161849"
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
[Issame:: Value](#value) | 表示一種型別是否與另一個相同。

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
