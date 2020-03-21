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
ms.openlocfilehash: 09819c9e8dd924581ce8cd67233d273f7e8d62ca
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079902"
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
非同步作業完成時呼叫的事件處理常式。

*TProgress*<br/>
當執行中的非同步作業報告作業的目前進度時，所呼叫的事件處理常式。

*resultType*<br/>
其中一個[AsyncResultType](asyncresulttype-enumeration.md)列舉值。 預設值為 `SingleResult`。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                               | 描述
---------------------------------- | -------------------------------------------------
[AsyncBase：： AsyncBase](#asyncbase) | 初始化 `AsyncBase` 類別的執行個體。

### <a name="public-methods"></a>公用方法

名稱                                         | 描述
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase：： Cancel](#cancel)                 | 取消非同步作業。
[AsyncBase：： Close](#close)                   | 關閉非同步作業。
[AsyncBase：： FireCompletion](#firecompletion) | 叫用完成事件處理常式，或重設內部進度委派。
[AsyncBase：： FireProgress](#fireprogress)     | 叫用目前的進度事件處理常式。
[AsyncBase：： get_ErrorCode](#get-errorcode)   | 抓取目前非同步作業的錯誤碼。
[AsyncBase：： get_Id](#get-id)                 | 抓取非同步作業的控制碼。
[AsyncBase：： get_Status](#get-status)         | 抓取值，指出非同步作業的狀態。
[AsyncBase：： GetOnComplete](#getoncomplete)   | 將目前完成事件處理常式的位址複製到指定的變數。
[AsyncBase：： GetOnProgress](#getonprogress)   | 將目前進度事件處理常式的位址複製到指定的變數。
[AsyncBase：:p ut_Id](#put-id)                 | 設定非同步作業的控制碼。
[AsyncBase：:P utOnComplete](#putoncomplete)   | 將完成事件處理常式的位址設定為指定的值。
[AsyncBase：:P utOnProgress](#putonprogress)   | 將進度事件處理常式的位址設定為指定的值。

### <a name="protected-methods"></a>受保護的方法

名稱                                                                         | 描述
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase：： CheckValidStateForDelegateCall](#checkvalidstatefordelegatecall) | 測試委派屬性是否可以在目前的非同步狀態中修改。
[AsyncBase：： CheckValidStateForResultsCall](#checkvalidstateforresultscall)   | 測試是否可以在目前的非同步狀態中收集非同步作業的結果。
[AsyncBase：： ContinueAsyncOperation](#continueasyncoperation)                 | 判斷非同步作業是否應該繼續處理，或應停止。
[AsyncBase：： CurrentStatus](#currentstatus)                                   | 抓取目前非同步作業的狀態。
[AsyncBase：： ErrorCode](#errorcode)                                           | 抓取目前非同步作業的錯誤碼。
[AsyncBase：： OnCancel](#oncancel)                                             | 在衍生類別中覆寫時，取消非同步作業。
[AsyncBase：： OnClose](#onclose)                                               | 在衍生類別中覆寫時，關閉非同步作業。
[AsyncBase：： OnStart](#onstart)                                               | 在衍生類別中覆寫時，啟動非同步作業。
[AsyncBase：： Start](#start)                                                   | 啟動非同步作業。
[AsyncBase：： TryTransitionToCompleted](#trytransitiontocompleted)             | 指出目前的非同步作業是否已完成。
[AsyncBase：： TryTransitionToError](#trytransitiontoerror)                     | 指出指定的錯誤碼是否可以修改內部錯誤狀態。

## <a name="inheritance-hierarchy"></a>繼承階層

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>需求

**標頭：** async。h

**命名空間：** Microsoft::WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a>AsyncBase：： AsyncBase

初始化 `AsyncBase` 類別的執行個體。

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a>AsyncBase：： Cancel

取消非同步作業。

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>傳回值

根據預設，一律會傳回 S_OK。

### <a name="remarks"></a>備註

`Cancel()` 是 `IAsyncInfo::Cancel`的預設實值，而且沒有實際的工作。 若要實際取消非同步作業，請覆寫 `OnCancel()` 純虛擬方法。

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a>AsyncBase：： CheckValidStateForDelegateCall

測試委派屬性是否可以在目前的非同步狀態中修改。

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>傳回值

S_OK 是否可以修改委派屬性;否則，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a>AsyncBase：： CheckValidStateForResultsCall

測試是否可以在目前的非同步狀態中收集非同步作業的結果。

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>傳回值

S_OK 是否可以收集結果;否則，E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseclose"></a><a name="close"></a>AsyncBase：： Close

關閉非同步作業。

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>傳回值

S_OK，如果作業關閉或已關閉，則為，否則，E_ILLEGAL_STATE_CHANGE。

### <a name="remarks"></a>備註

`Close()` 是 `IAsyncInfo::Close`的預設實值，而且沒有實際的工作。 若要實際關閉非同步作業，請覆寫 `OnClose()` 純虛擬方法。

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a>AsyncBase：： ContinueAsyncOperation

判斷非同步作業是否應該繼續處理，或應停止。

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>傳回值

如果非同步作業的目前狀態是 [*已啟動*]，則**為 true** ，表示作業應該繼續進行。 否則為**false**，表示應該停止作業。

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a>AsyncBase：： CurrentStatus

抓取目前非同步作業的狀態。

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>參數

*status*<br/>
此作業儲存目前狀態的位置。

### <a name="remarks"></a>備註

這是安全線程。

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a>AsyncBase：： ErrorCode

抓取目前非同步作業的錯誤碼。

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>參數

*error*<br/>
此作業用來儲存目前錯誤碼的位置。

### <a name="remarks"></a>備註

這是安全線程。

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a>AsyncBase：： FireCompletion

叫用完成事件處理常式，或重設內部進度委派。

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>備註

第一個版本的 `FireCompletion()` 重設內部進度委派變數。 如果非同步作業已完成，則第二個版本會叫用完成事件處理常式。

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a>AsyncBase：： FireProgress

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

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a>AsyncBase：： get_ErrorCode

抓取目前非同步作業的錯誤碼。

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>參數

*錯誤碼*<br/>
儲存目前錯誤碼的位置。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，如果目前的非同步作業已關閉，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseget_id"></a><a name="get-id"></a>AsyncBase：： get_Id

抓取非同步作業的控制碼。

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>參數

*id*<br/>
要儲存控制碼的位置。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，E_ILLEGAL_METHOD_CALL。

### <a name="remarks"></a>備註

這個方法會實作 `IAsyncInfo::get_Id`。

## <a name="asyncbaseget_status"></a><a name="get-status"></a>AsyncBase：： get_Status

抓取值，指出非同步作業的狀態。

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>參數

*status*<br/>
要儲存狀態的位置。 如需詳細資訊，請參閱 `Windows::Foundation::AsyncStatus` 列舉。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，E_ILLEGAL_METHOD_CALL。

### <a name="remarks"></a>備註

這個方法會實作 `IAsyncInfo::get_Status`。

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a>AsyncBase：： GetOnComplete

將目前完成事件處理常式的位址複製到指定的變數。

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>參數

*completeHandler*<br/>
儲存目前完成事件處理常式之位址的位置。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a>AsyncBase：： GetOnProgress

將目前進度事件處理常式的位址複製到指定的變數。

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>參數

*progressHandler*<br/>
儲存目前進度事件處理常式之位址的位置。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a>AsyncBase：： OnCancel

在衍生類別中覆寫時，取消非同步作業。

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a>AsyncBase：： OnClose

在衍生類別中覆寫時，關閉非同步作業。

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a>AsyncBase：： OnStart

在衍生類別中覆寫時，啟動非同步作業。

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a>AsyncBase：:p ut_Id

設定非同步作業的控制碼。

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>參數

*id*<br/>
非零的控制碼。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，E_INVALIDARG 或 E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a>AsyncBase：:P utOnComplete

將完成事件處理常式的位址設定為指定的值。

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>參數

*completeHandler*<br/>
完成事件處理常式設定的位址。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a>AsyncBase：:P utOnProgress

將進度事件處理常式的位址設定為指定的值。

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>參數

*progressHandler*<br/>
進度事件處理常式所設定的位址。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，E_ILLEGAL_METHOD_CALL。

## <a name="asyncbasestart"></a><a name="start"></a>AsyncBase：： Start

啟動非同步作業。

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>傳回值

S_OK，如果作業開始或已啟動，則為，否則，E_ILLEGAL_STATE_CHANGE。

### <a name="remarks"></a>備註

`Start()` 是受保護的方法，不是外部可見的，因為非同步作業會在傳回呼叫端之前「暖開機」。

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a>AsyncBase：： TryTransitionToCompleted

指出目前的非同步作業是否已完成。

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>傳回值

如果非同步作業已完成，則為**true** ;否則**為 false**。

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a>AsyncBase：： TryTransitionToError

指出指定的錯誤碼是否可以修改內部錯誤狀態。

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>參數

*error*<br/>
錯誤 HRESULT。

### <a name="return-value"></a>傳回值

如果內部錯誤狀態已變更，則**為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

只有當錯誤狀態已設定為 [S_OK] 時，此作業才會修改錯誤狀態。 如果錯誤狀態為 [錯誤]、[已取消]、[已完成] 或 [已關閉]，則此作業沒有作用。
