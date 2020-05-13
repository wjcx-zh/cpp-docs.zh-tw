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
ms.openlocfilehash: 16c44d861ebbbc98fa1bffb62a00d1989c0c803c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377164"
---
# <a name="argtraits-structure"></a>ArgTraits 結構

支援 WRL 基礎結構,不打算直接從代碼中使用。

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

*T成員功能*<br/>
ArgTraits 結構的類型名稱參數,該結構無法與`Invoke`任何 方法簽名匹配。

*T委託介面*<br/>
委託介面。

*TArg1*<br/>
`Invoke`方法的第一個參數的類型。

*TArg2*<br/>
`Invoke`方法的第二個參數的類型。

*TArg3*<br/>
`Invoke`方法的第三個參數的類型。

*TArg4*<br/>
`Invoke`方法的第四個參數的類型。

*TArg5*<br/>
`Invoke`方法的第五個參數的類型。

*TArg6*<br/>
`Invoke`方法的第六個參數的類型。

*TArg7*<br/>
`Invoke`方法的第七個參數的類型。

*TArg8*<br/>
`Invoke`方法的第八個參數的類型。

*TArg9*<br/>
`Invoke`方法的第九個參數的類型。

## <a name="remarks"></a>備註

結構`ArgTraits`聲明指定的委託介面和具有指定數量的參數的匿名成員函數。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱       | 描述
---------- | ----------------------
`Arg1Type` | TArg1 的類型def。
`Arg2Type` | TArg2 的類型def。
`Arg3Type` | TArg3 的類型def。
`Arg4Type` | TArg4 的類型def。
`Arg5Type` | TArg5 的類型def。
`Arg6Type` | TArg6 的類型def。
`Arg7Type` | TArg7 的類型def。
`Arg8Type` | TArg8 的類型def。
`Arg9Type` | TArg9 的類型def。

### <a name="public-constants"></a>公用常數

名稱                     | 描述
------------------------ | ---------------------------------------------------------------------------------------
[阿格格茨:阿格茨](#args) | 在委託介面`Invoke`的方法上保留參數數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ArgTraits`

## <a name="requirements"></a>需求

**標題:** 事件.h

**命名空間:** 微軟::WRL::D

## <a name="argtraitsargs"></a><a name="args"></a>阿格格茨:阿格茨

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
static const int args = -1;
```

### <a name="remarks"></a>備註

在委託介面`Invoke`的方法上保留參數數。 當`args`等於 -1`Invoke`時, 方法簽名不能匹配。
