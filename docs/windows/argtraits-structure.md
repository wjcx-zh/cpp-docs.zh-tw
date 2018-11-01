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
ms.openlocfilehash: 17109508cf99888ccde79be39a41c5361da24c6e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549005"
---
# <a name="argtraits-structure"></a>ArgTraits 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

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
Typename 參數不符合任何 ArgTraits 結構`Invoke`方法簽章。

*TDelegateInterface*<br/>
委派的介面。

*TArg1*<br/>
第一個引數型別`Invoke`方法。

*TArg2*<br/>
第二個引數型別`Invoke`方法。

*TArg3*<br/>
第三個引數型別`Invoke`方法。

*TArg4*<br/>
第四個引數型別`Invoke`方法。

*TArg5*<br/>
第五個引數型別`Invoke`方法。

*TArg6*<br/>
第六個引數型別`Invoke`方法。

*TArg7*<br/>
第七個引數型別`Invoke`方法。

*TArg8*<br/>
第八個引數型別`Invoke`方法。

*TArg9*<br/>
第九個引數型別`Invoke`方法。

## <a name="remarks"></a>備註

`ArgTraits`結構宣告指定的委派，介面和匿名的成員函式具有指定的參數數目。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱       | 描述
---------- | ----------------------
`Arg1Type` | TArg1 typedef。
`Arg2Type` | TArg2 typedef。
`Arg3Type` | TArg3 typedef。
`Arg4Type` | TArg4 typedef。
`Arg5Type` | TArg5 typedef。
`Arg6Type` | TArg6 typedef。
`Arg7Type` | TArg7 typedef。
`Arg8Type` | TArg8 typedef。
`Arg9Type` | TArg9 typedef。

### <a name="public-constants"></a>公用常數

名稱                     | 描述
------------------------ | ---------------------------------------------------------------------------------------
[Argtraits:: Args](#args) | 將保存的參數數目的計數`Invoke`委派介面的方法。

## <a name="inheritance-hierarchy"></a>繼承階層

`ArgTraits`

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL::Details

## <a name="args"></a>Argtraits:: Args

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
static const int args = -1;
```

### <a name="remarks"></a>備註

將保存的參數數目的計數`Invoke`委派介面的方法。 當`args`等於-1，可針對沒有相符項目`Invoke`方法簽章。
