---
title: ArgTraitsHelper 結構 |Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraitsHelper structure
- Microsoft::WRL::Details::ArgTraitsHelper::args constant
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b608f5da893019d7700891968dcdc06489c563ea
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234225"
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
[Argtraitshelper:: Args](#args) | 可協助[argtraits:: Args](#args)上保留的參數數目的計數`Invoke`委派介面的方法。

## <a name="inheritance-hierarchy"></a>繼承階層

`ArgTraitsHelper`

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL::Details

## <a name="args"></a>Argtraitshelper:: Args

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>備註

可協助`ArgTraitsHelper::args`保留的參數數目的計數上`Invoke`委派介面的方法。
