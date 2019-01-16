---
title: AsyncBase 類別
ms.date: 10/08/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
- async/Microsoft::WRL::AsyncBase::AsyncBase
- async/Microsoft::WRL::AsyncBase::Cancel
- async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
- async/Microsoft::WRL::AsyncBase::Close
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
- async/Microsoft::WRL::AsyncBase::CurrentStatus
- async/Microsoft::WRL::AsyncBase::ErrorCode
- async/Microsoft::WRL::AsyncBase::FireCompletion
- async/Microsoft::WRL::AsyncBase::FireProgress
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
- async/Microsoft::WRL::AsyncBase::get_Id
- async/Microsoft::WRL::AsyncBase::get_Status
- async/Microsoft::WRL::AsyncBase::GetOnComplete
- async/Microsoft::WRL::AsyncBase::GetOnProgress
- async/Microsoft::WRL::AsyncBase::OnCancel
- async/Microsoft::WRL::AsyncBase::OnClose
- async/Microsoft::WRL::AsyncBase::OnStart
- async/Microsoft::WRL::AsyncBase::put_Id
- async/Microsoft::WRL::AsyncBase::PutOnComplete
- async/Microsoft::WRL::AsyncBase::PutOnProgress
- async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
helpviewer_keywords:
- Microsoft::WRL::AsyncBase class
- Microsoft::WRL::AsyncBase::AsyncBase, constructor
- Microsoft::WRL::AsyncBase::Cancel method
- Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall method
- Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall method
- Microsoft::WRL::AsyncBase::Close method
- Microsoft::WRL::AsyncBase::ContinueAsyncOperation method
- Microsoft::WRL::AsyncBase::CurrentStatus method
- Microsoft::WRL::AsyncBase::ErrorCode method
- Microsoft::WRL::AsyncBase::FireCompletion method
- Microsoft::WRL::AsyncBase::FireProgress method
- Microsoft::WRL::AsyncBase::get_ErrorCode method
- Microsoft::WRL::AsyncBase::get_Id method
- Microsoft::WRL::AsyncBase::get_Status method
- Microsoft::WRL::AsyncBase::GetOnComplete method
- Microsoft::WRL::AsyncBase::GetOnProgress method
- Microsoft::WRL::AsyncBase::OnCancel method
- Microsoft::WRL::AsyncBase::OnClose method
- Microsoft::WRL::AsyncBase::OnStart method
- Microsoft::WRL::AsyncBase::put_Id method
- Microsoft::WRL::AsyncBase::PutOnComplete method
- Microsoft::WRL::AsyncBase::PutOnProgress method
- Microsoft::WRL::AsyncBase::TryTransitionToCompleted method
- Microsoft::WRL::AsyncBase::TryTransitionToError method
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
ms.openlocfilehash: 367d0b0cd3197623b27ee1a50e804cca797aedf3
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335718"
---
# <a name="asyncbase-class"></a>AsyncBase 類別

實作 Windows 執行階段非同步狀態機器。

## <a name="syntax"></a>語法

```cpp
template <
    typename TComplete,
    typename TProgress = Details::Nil,
    AsyncResultType resultType = SingleResult
>
class AsyncBase : public AsyncBase<TComplete, Details::Nil, resultType>;

template <typename TComplete, AsyncResultType resultType>
class AsyncBase<TComplete, Details::Nil, resultType> :
    public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>參數

*TComplete*<br/>
在非同步作業完成時，會呼叫事件處理常式。

*TProgress*<br/>
在執行中的非同步作業報告目前進度的作業時，會呼叫事件處理常式。

*resultType*<br/>
其中一個[AsyncResultType](asyncresulttype-enumeration.md)列舉值。 根據預設， `SingleResult`。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                               | 描述
---------------------------------- | -------------------------------------------------
[AsyncBase::AsyncBase](#asyncbase) | 初始化 `AsyncBase` 類別的執行個體。

### <a name="public-methods"></a>公用方法

名稱                                         | 描述
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase::Cancel](#cancel)                 | 取消非同步作業。
[AsyncBase::Close](#close)                   | 關閉的非同步作業。
[AsyncBase::FireCompletion](#firecompletion) | 叫用完成事件處理常式，或重設內部進行委派。
[AsyncBase::FireProgress](#fireprogress)     | 叫用目前的進度事件處理常式。
[AsyncBase::get_ErrorCode](#get-errorcode)   | 擷取目前的非同步作業的錯誤碼。
[AsyncBase::get_Id](#get-id)                 | 擷取非同步作業的控制代碼。
[AsyncBase::get_Status](#get-status)         | 擷取值，指出非同步作業的狀態。
[AsyncBase::GetOnComplete](#getoncomplete)   | 將目前的 「 完成 」 事件處理常式的位址複製到指定的變數中。
[AsyncBase::GetOnProgress](#getonprogress)   | 將目前的進度事件處理常式的位址複製到指定的變數中。
[AsyncBase::put_Id](#put-id)                 | 設定非同步作業的控制代碼。
[AsyncBase::PutOnComplete](#putoncomplete)   | 指定的值設定完成事件處理常式的位址。
[AsyncBase::PutOnProgress](#putonprogress)   | 指定的值設定進度事件處理常式的位址。


### <a name="protected-methods"></a>保護方法

名稱                                                                         | 描述
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase::CheckValidStateForDelegateCall](#checkvalidstatefordelegatecall) | 測試是否可以修改委派屬性，在目前的非同步狀態。
[AsyncBase::CheckValidStateForResultsCall](#checkvalidstateforresultscall)   | 測試是否可以收集在目前的非同步狀態中的非同步作業的結果。
[AsyncBase::ContinueAsyncOperation](#continueasyncoperation)                 | 判斷是否應該繼續處理非同步作業，或應該停止。
[AsyncBase::CurrentStatus](#currentstatus)                                   | 擷取目前的非同步作業的狀態。
[AsyncBase::ErrorCode](#errorcode)                                           | 擷取目前的非同步作業的錯誤碼。
[AsyncBase::OnCancel](#oncancel)                                             | 當在衍生類別中覆寫時，取消非同步作業。
[AsyncBase::OnClose](#onclose)                                               | 當在衍生類別中覆寫時，會關閉的非同步作業。
[AsyncBase::OnStart](#onstart)                                               | 當在衍生類別中覆寫時，會啟動非同步作業。
[AsyncBase::Start](#start)                                                   | 啟動非同步作業。
[AsyncBase::TryTransitionToCompleted](#trytransitiontocompleted)             | 表示目前的非同步作業是否已完成。
[AsyncBase::TryTransitionToError](#trytransitiontoerror)                     | 指出指定的錯誤程式碼是否可以修改的內部錯誤狀態。

## <a name="inheritance-hierarchy"></a>繼承階層

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>需求

**標頭：** async.h

**命名空間：** Microsoft:: wrl

## <a name="asyncbase"></a>AsyncBase::AsyncBase

初始化 `AsyncBase` 類別的執行個體。

```cpp
AsyncBase();
```

## <a name="cancel"></a>AsyncBase::Cancel

取消非同步作業。

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>傳回值

根據預設，一律會傳回 S_OK。

### <a name="remarks"></a>備註

`Cancel()` 預設實作`IAsyncInfo::Cancel`，並不執行任何實際工作。 若要實際取消非同步作業，請覆寫`OnCancel()`純虛擬方法。

## <a name="checkvalidstatefordelegatecall"></a>AsyncBase::CheckValidStateForDelegateCall

測試是否可以修改委派屬性，在目前的非同步狀態。

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>傳回值

如果可以修改委派屬性，為 S_OK否則，E_ILLEGAL_METHOD_CALL。

## <a name="checkvalidstateforresultscall"></a>AsyncBase::CheckValidStateForResultsCall

測試是否可以收集在目前的非同步狀態中的非同步作業的結果。

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>傳回值

如果可以收集結果;，為 S_OK否則，E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL。

## <a name="close"></a>AsyncBase::Close

關閉的非同步作業。

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>傳回值

S_OK，如果作業會關閉或已關閉否則，E_ILLEGAL_STATE_CHANGE。

### <a name="remarks"></a>備註

`Close()` 預設實作`IAsyncInfo::Close`，並不執行任何實際工作。 若要實際關閉非同步作業，請覆寫`OnClose()`純虛擬方法。

## <a name="continueasyncoperation"></a>AsyncBase::ContinueAsyncOperation

判斷是否應該繼續處理非同步作業，或應該停止。

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>傳回值

**真**非同步作業的目前狀態是否*啟動*，這表示作業應該繼續。 否則，請**false**，這表示作業應該停止。

## <a name="currentstatus"></a>AsyncBase::CurrentStatus

擷取目前的非同步作業的狀態。

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>參數

*status*<br/>
這項作業儲存的目前狀態的位置。

### <a name="remarks"></a>備註

這項作業是安全執行緒。

## <a name="errorcode"></a>AsyncBase::ErrorCode

擷取目前的非同步作業的錯誤碼。

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>參數

*error*<br/>
這項作業儲存目前的錯誤程式碼的位置。

### <a name="remarks"></a>備註

這項作業是安全執行緒。

## <a name="firecompletion"></a>AsyncBase::FireCompletion

叫用完成事件處理常式，或重設內部進行委派。

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>備註

第一版`FireCompletion()`重設內部進行委派變數。 如果非同步作業已完成，則第二個版本會叫用完成事件處理常式。

## <a name="fireprogress"></a>AsyncBase::FireProgress

叫用目前的進度事件處理常式。

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>參數

*arg*<br/>
要叫用的事件處理常式方法。

### <a name="remarks"></a>備註

`ProgressTraits` 衍生自[ArgTraitsHelper 結構](argtraitshelper-structure.md)。

## <a name="get-errorcode"></a>AsyncBase::get_ErrorCode

擷取目前的非同步作業的錯誤碼。

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>參數

*errorCode*<br/>
儲存目前的錯誤程式碼位置。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，如果目前的非同步作業已關閉的 E_ILLEGAL_METHOD_CALL。

## <a name="get-id"></a>AsyncBase::get_Id

擷取非同步作業的控制代碼。

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>參數

*id*<br/>
控制代碼之儲存位置。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，E_ILLEGAL_METHOD_CALL。

### <a name="remarks"></a>備註

這個方法會實作 `IAsyncInfo::get_Id`。

## <a name="get-status"></a>AsyncBase::get_Status

擷取值，指出非同步作業的狀態。

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>參數

*status*<br/>
儲存狀態的位置。 如需詳細資訊，請參閱`Windows::Foundation::AsyncStatus`列舉型別。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，E_ILLEGAL_METHOD_CALL。

### <a name="remarks"></a>備註

這個方法會實作 `IAsyncInfo::get_Status`。

## <a name="getoncomplete"></a>AsyncBase::GetOnComplete

將目前的 「 完成 」 事件處理常式的位址複製到指定的變數中。

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>參數

*completeHandler*<br/>
目前的 「 完成 」 事件處理常式的位址儲存位置。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，E_ILLEGAL_METHOD_CALL。

## <a name="getonprogress"></a>AsyncBase::GetOnProgress

將目前的進度事件處理常式的位址複製到指定的變數中。

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>參數

*progressHandler*<br/>
目前的進度事件處理常式的位址儲存位置。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，E_ILLEGAL_METHOD_CALL。

## <a name="oncancel"></a>AsyncBase::OnCancel

當在衍生類別中覆寫時，取消非同步作業。

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="onclose"></a>AsyncBase::OnClose

當在衍生類別中覆寫時，會關閉的非同步作業。

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="onstart"></a>AsyncBase::OnStart

當在衍生類別中覆寫時，會啟動非同步作業。

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="put-id"></a>AsyncBase::put_Id

設定非同步作業的控制代碼。

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>參數

*id*<br/>
非零的控制代碼。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則 E_INVALIDARG 或 E_ILLEGAL_METHOD_CALL。

## <a name="putoncomplete"></a>AsyncBase::PutOnComplete

指定的值設定完成事件處理常式的位址。

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>參數

*completeHandler*<br/>
設定完成事件處理常式的位址。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，E_ILLEGAL_METHOD_CALL。

## <a name="putonprogress"></a>AsyncBase::PutOnProgress

指定的值設定進度事件處理常式的位址。

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>參數

*progressHandler*<br/>
設定進度事件處理常式的位址。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，E_ILLEGAL_METHOD_CALL。

## <a name="start"></a>AsyncBase::Start

啟動非同步作業。

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>傳回值

S_OK 如果作業啟動或已啟動;否則，E_ILLEGAL_STATE_CHANGE。

### <a name="remarks"></a>備註

`Start()` 是受保護的方法，不是外部可見因為非同步作業 「 經常性開始 」，然後傳回給呼叫端。

## <a name="trytransitiontocompleted"></a>AsyncBase::TryTransitionToCompleted

表示目前的非同步作業是否已完成。

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>傳回值

**true**如果非同步作業完成為止，否則**false**。

## <a name="trytransitiontoerror"></a>AsyncBase::TryTransitionToError

指出指定的錯誤程式碼是否可以修改的內部錯誤狀態。

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>參數

*error*<br/>
錯誤的 HRESULT。

### <a name="return-value"></a>傳回值

**真**如果內部錯誤狀態已變更，否則**false**。

### <a name="remarks"></a>備註

這項作業會在錯誤狀態已設為 S_OK 時，才修改錯誤狀態。 如果錯誤的狀態已取消、 已完成，或關閉的錯誤，這項作業會有任何作用。
