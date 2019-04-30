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
ms.openlocfilehash: 3fcba210d4018d22487d234b437acfee3634cec6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386131"
---
# <a name="invokehelper-structure"></a>InvokeHelper 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

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

*TDelegateInterface*<br/>
委派的介面型別。

*TCallback*<br/>
事件處理常式函式的類型。

*argCount*<br/>
中的引數數目`InvokeHelper`特製化。

## <a name="remarks"></a>備註

提供實作`Invoke()`方法根據指定的數目和類型的引數。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱     | 描述
-------- | -----------------------------------------------------------------------------
`Traits` | 類別定義的每個事件處理常式的引數類型同義。

### <a name="public-constructors"></a>公用建構函式

名稱                                        | 描述
------------------------------------------- | -------------------------------------------------------
[InvokeHelper::InvokeHelper](#invokehelper) | 初始化 `InvokeHelper` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                            | 描述
------------------------------- | -----------------------------------------------------------------------------------
[InvokeHelper::Invoke](#invoke) | 會呼叫其簽章包含指定的引數的事件處理常式。

### <a name="public-data-members"></a>公用資料成員

名稱                                 | 描述
------------------------------------ | ----------------------------------------------------------
[InvokeHelper::callback_](#callback) | 表示事件發生時要呼叫的事件處理常式。

## <a name="inheritance-hierarchy"></a>繼承階層

`InvokeHelper`

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL::Details

## <a name="callback"></a>Invokehelper:: Callback_

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
TCallback callback_;
```

### <a name="remarks"></a>備註

表示事件發生時要呼叫的事件處理常式。

`TCallback`範本參數會指定事件處理常式的類型。

## <a name="invoke"></a>InvokeHelper::Invoke

支援 WRL 結構，而且不是直接從您的程式碼使用。

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
引數 1。

*arg2*<br/>
引數 2。

*arg3*<br/>
引數 3。

*arg4*<br/>
引數 4。

*arg5*<br/>
引數 5。

*arg6*<br/>
引數 6。

*arg7*<br/>
引數 7。

*arg8*<br/>
引數 8。

*arg9*<br/>
引數 9。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，會描述錯誤的 HRESULT。

### <a name="remarks"></a>備註

會呼叫其簽章包含指定的引數的事件處理常式。

## <a name="invokehelper"></a>InvokeHelper::InvokeHelper

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>參數

*callback*<br/>
事件處理常式。

### <a name="remarks"></a>備註

初始化 `InvokeHelper` 類別的新執行個體。

`TCallback`範本參數會指定事件處理常式的類型。
