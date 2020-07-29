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
ms.openlocfilehash: 8c209d5a8d2a35f2643e90e5595d86f41519f30b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216553"
---
# <a name="issame-structure"></a>IsSame 結構

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

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

測試一個指定的類型是否與另一個指定的類型相同。

## <a name="members"></a>成員

### <a name="public-constants"></a>公用常數

名稱                    | 說明
----------------------- | --------------------------------------------------
[IsSame：： value](#value) | 指出某個類型是否與另一個型別相同。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IsSame`

## <a name="requirements"></a>需求

**標頭：** 內部。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="issamevalue"></a><a name="value"></a>IsSame：： value

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

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

指出某個類型是否與另一個型別相同。

`value`**`true`** 如果範本參數相同，而且樣板參數不同，則為 **`false`** 。
