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
ms.openlocfilehash: fcaf33309521b44163022e0ffa9b1e03e53e2551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371339"
---
# <a name="issame-structure"></a>IsSame 結構

支援 WRL 基礎結構,不打算直接從代碼中使用。

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
另一種類型。

## <a name="remarks"></a>備註

測試一個指定類型是否與另一個指定類型相同。

## <a name="members"></a>成員

### <a name="public-constants"></a>公用常數

名稱                    | 描述
----------------------- | --------------------------------------------------
[相同:值](#value) | 指示一種類型是否與另一種類型相同。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IsSame`

## <a name="requirements"></a>需求

**標題:** 內部.h

**命名空間:** 微軟::WRL::D

## <a name="issamevalue"></a><a name="value"></a>相同:值

支援 WRL 基礎結構,不打算直接從代碼中使用。

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

指示一種類型是否與另一種類型相同。

`value`如果樣本參數相同,**則為 true;** 如果樣本參數不同,**則為 false。**
