---
title: ArgTraitsHelper 結構
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraitsHelper structure
- Microsoft::WRL::Details::ArgTraitsHelper::args constant
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
ms.openlocfilehash: 4acbd9fa660f29bbaf209282ff0e90f43621574d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360775"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper 結構

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>參數

*T委託介面*<br/>
委託介面。

## <a name="remarks"></a>備註

幫助定義委託參數的常見特徵。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱         | 描述
------------ | ------------------------------------------------------
`methodType` | `decltype(&TDelegateInterface::Invoke)` 的同義字。
`Traits`     | `ArgTraits<methodType>` 的同義字。

### <a name="public-constants"></a>公用常數

名稱                           | 描述
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[阿格·格薩爾特説明者::阿格斯](#args) | 説明[ArgTraits::args](#args)在`Invoke`委託介面 的方法上保留參數數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ArgTraitsHelper`

## <a name="requirements"></a>需求

**標題:** 事件.h

**命名空間:** 微軟::WRL::D

## <a name="argtraitshelperargs"></a><a name="args"></a>阿格·格薩爾特説明者::阿格斯

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>備註

説明`ArgTraitsHelper::args`保留委託介面方法`Invoke`上的 參數數。
