---
title: InvokeHelper 結構
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
ms.openlocfilehash: 9cb4e166628a6b5e7671494446d467e73c9f8cc3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371378"
---
# <a name="invokehelper-structure"></a>InvokeHelper 結構

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
template<typename TDelegateInterface, typename TCallback, unsigned int argCount>
struct InvokeHelper;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 0> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 1> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 2> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 3> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 4> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 5> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 6> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 7> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 8> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 9> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;
```

### <a name="parameters"></a>參數

*T委託介面*<br/>
委託介面類型。

*回撥*<br/>
事件處理程式函數的類型。

*arg( A) Counts*<br/>
`InvokeHelper`專門化中的參數數。

## <a name="remarks"></a>備註

根據指定的參數數和`Invoke()`類型提供方法的實現。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱     | 描述
-------- | -----------------------------------------------------------------------------
`Traits` | 定義每個事件處理程式參數類型的類的同義詞。

### <a name="public-constructors"></a>公用建構函式

名稱                                        | 描述
------------------------------------------- | -------------------------------------------------------
[呼叫説明者::呼叫說明程式](#invokehelper) | 將 `InvokeHelper` 類別的新執行個體初始化。

### <a name="public-methods"></a>公用方法

名稱                            | 描述
------------------------------- | -----------------------------------------------------------------------------------
[呼叫輔助器::呼叫](#invoke) | 呼叫其簽署包含指定參數數的事件處理程式。

### <a name="public-data-members"></a>公用資料成員

名稱                                 | 描述
------------------------------------ | ----------------------------------------------------------
[呼叫説明者::callback_](#callback) | 表示事件發生時要調用的事件處理程式。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`InvokeHelper`

## <a name="requirements"></a>需求

**標題:** 事件.h

**命名空間:** 微軟::WRL::D

## <a name="invokehelpercallback_"></a><a name="callback"></a>呼叫説明者::callback_

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
TCallback callback_;
```

### <a name="remarks"></a>備註

表示事件發生時要調用的事件處理程式。

樣本`TCallback`參數指定事件處理程式的類型。

## <a name="invokehelperinvoke"></a><a name="invoke"></a>呼叫輔助器::呼叫

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
STDMETHOD(
   Invoke
)();
STDMETHOD(
   Invoke
)(typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
```

### <a name="parameters"></a>參數

*arg1*<br/>
參數 1.

*arg2*<br/>
參數 2.

*arg3*<br/>
參數 3.

*arg4*<br/>
參數 4.

*arg5*<br/>
參數 5.

*arg6*<br/>
參數 6.

*arg7*<br/>
參數 7.

*arg8*<br/>
參數 8.

*arg9*<br/>
參數 9.

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,描述錯誤的 HRESULT。

### <a name="remarks"></a>備註

呼叫其簽署包含指定參數數的事件處理程式。

## <a name="invokehelperinvokehelper"></a><a name="invokehelper"></a>呼叫説明者::呼叫說明程式

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>參數

*回撥*<br/>
事件處理常式。

### <a name="remarks"></a>備註

將 `InvokeHelper` 類別的新執行個體初始化。

樣本`TCallback`參數指定事件處理程式的類型。
