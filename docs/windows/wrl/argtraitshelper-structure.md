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
ms.openlocfilehash: fbba6d96106cc95910ccd9d0029cb3e9c254d7d3
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336389"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>參數

*TDelegateInterface*<br/>
委派的介面。

## <a name="remarks"></a>備註

可協助定義委派引數的一般的特性。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱         | 描述
------------ | ------------------------------------------------------
`methodType` | `decltype(&TDelegateInterface::Invoke)` 的同義字。
`Traits`     | `ArgTraits<methodType>` 的同義字。

### <a name="public-constants"></a>公用常數

名稱                           | 描述
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[ArgTraitsHelper::args](#args) | 可協助[argtraits:: Args](#args)上保留的參數數目的計數`Invoke`委派介面的方法。

## <a name="inheritance-hierarchy"></a>繼承階層

`ArgTraitsHelper`

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL::Details

## <a name="args"></a>ArgTraitsHelper::args

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>備註

可協助`ArgTraitsHelper::args`保留的參數數目的計數上`Invoke`委派介面的方法。
