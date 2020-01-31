---
title: ArgTraits 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits
- event/Microsoft::WRL::Details::ArgTraits::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraits structure
- Microsoft::WRL::Details::ArgTraits::args constant
ms.assetid: 58ae4115-c1bc-48c8-b01b-e60554841c30
ms.openlocfilehash: c13e7fec3289b66b40e44f91404a50cba7a473b1
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821710"
---
# <a name="argtraits-structure"></a>ArgTraits 結構

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template<typename TMemberFunction>
struct ArgTraits;

template<typename TDelegateInterface>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(void)>;

template<typename TDelegateInterface, typename TArg1>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1)>;

template<typename TDelegateInterface, typename TArg1, typename TArg2>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8, TArg9)>;
```

### <a name="parameters"></a>參數

*TMemberFunction*<br/>
無法比對任何 `Invoke` 方法簽章之 ArgTraits 結構的 Typename 參數。

*TDelegateInterface*<br/>
委派介面。

*TArg1*<br/>
`Invoke` 方法之第一個引數的型別。

*TArg2*<br/>
`Invoke` 方法的第二個引數的類型。

*TArg3*<br/>
`Invoke` 方法的第三個引數的類型。

*TArg4*<br/>
`Invoke` 方法的第四個引數的類型。

*TArg5*<br/>
`Invoke` 方法的第五個引數的類型。

*TArg6*<br/>
`Invoke` 方法的第六個引數的類型。

*TArg7*<br/>
`Invoke` 方法之第七個引數的類型。

*TArg8*<br/>
`Invoke` 方法的第八個引數的類型。

*TArg9*<br/>
`Invoke` 方法之第九個引數的類型。

## <a name="remarks"></a>備註

`ArgTraits` 結構會宣告指定的委派介面，以及具有指定之參數數目的匿名成員函式。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公用 Typedefs

Name       | 描述
---------- | ----------------------
`Arg1Type` | TArg1 的 typedef。
`Arg2Type` | TArg2 的 typedef。
`Arg3Type` | TArg3 的 typedef。
`Arg4Type` | TArg4 的 typedef。
`Arg5Type` | TArg5 的 typedef。
`Arg6Type` | TArg6 的 typedef。
`Arg7Type` | TArg7 的 typedef。
`Arg8Type` | TArg8 的 typedef。
`Arg9Type` | TArg9 的 typedef。

### <a name="public-constants"></a>公用常數

Name                     | 描述
------------------------ | ---------------------------------------------------------------------------------------
[ArgTraits：： args](#args) | 保留委派介面之 `Invoke` 方法上的參數數目計數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ArgTraits`

## <a name="requirements"></a>需求

**Header：** 事件。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="args"></a>ArgTraits：： args

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
static const int args = -1;
```

### <a name="remarks"></a>備註

保留委派介面之 `Invoke` 方法上的參數數目計數。 當 `args` 等於-1 時，不會有 `Invoke` 方法簽章的相符項。
