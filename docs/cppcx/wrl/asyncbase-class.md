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
ms.openlocfilehash: 0254aa4dc243eeffa43850c437a833a6530c01e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371865"
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

*完成*<br/>
非同步操作完成後調用的事件處理程式。

*T進展*<br/>
運行非同步操作報告操作的當前進度時調用的事件處理程式。

*結果類型*<br/>
[AsyncResult 類型](asyncresulttype-enumeration.md)枚舉值之一。 預設值為 `SingleResult`。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                               | 描述
---------------------------------- | -------------------------------------------------
[非同步基礎::非同步基礎](#asyncbase) | 初始化 `AsyncBase` 類別的執行個體。

### <a name="public-methods"></a>公用方法

名稱                                         | 描述
-------------------------------------------- | -------------------------------------------------------------------------------------
[非同步基礎::取消](#cancel)                 | 取消非同步操作。
[非同步基礎:關閉](#close)                   | 關閉非同步操作。
[非同步基礎::火完成](#firecompletion) | 調用完成事件處理程式,或重置內部進度委託。
[非同步基礎::火進度](#fireprogress)     | 調用當前進度事件處理程式。
[非同步基礎::get_ErrorCode](#get-errorcode)   | 檢索當前非同步操作的錯誤代碼。
[非同步基礎::get_Id](#get-id)                 | 檢索異步操作的句柄。
[非同步基礎::get_Status](#get-status)         | 檢索指示異步操作狀態的值。
[非同步基礎::完成](#getoncomplete)   | 將目前完成事件處理程式的位址複製到指定的變數。
[非同步基礎::取得進度](#getonprogress)   | 將當前進度事件處理程式的位址複製到指定的變數。
[非同步基礎::put_Id](#put-id)                 | 設置非同步操作的句柄。
[非同步基礎::PutOnComplete](#putoncomplete)   | 將完成事件處理程式的位址設置為指定值。
[非同步基礎::P](#putonprogress)   | 將進度事件處理程式的位址設置為指定值。

### <a name="protected-methods"></a>保護方法

名稱                                                                         | 描述
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[非同步基礎::檢查有效狀態的委託呼叫](#checkvalidstatefordelegatecall) | 測試是否可以在當前異步狀態下修改委託屬性。
[非同步基礎::檢查有效狀態結果呼叫](#checkvalidstateforresultscall)   | 測試非同步操作的結果是否可以在當前異步狀態下收集。
[非同步的基礎:繼續同步操作](#continueasyncoperation)                 | 確定非同步操作是繼續處理還是應停止。
[非同步基礎::當前狀態](#currentstatus)                                   | 檢索當前異步操作的狀態。
[非同步基礎::錯誤代碼](#errorcode)                                           | 檢索當前非同步操作的錯誤代碼。
[非同步基礎::開啟取消](#oncancel)                                             | 在派生類中重寫時,將取消非同步操作。
[非同步基礎:關閉](#onclose)                                               | 在派生類中重寫時,將關閉非同步操作。
[非同步基礎::開始](#onstart)                                               | 在派生類中重寫時,啟動非同步操作。
[非同步基礎::開始](#start)                                                   | 啟動非同步操作。
[非同步基礎::嘗試過渡完成](#trytransitiontocompleted)             | 指示當前非同步操作是否已完成。
[非同步基礎::嘗試轉換到錯誤](#trytransitiontoerror)                     | 指示指定的錯誤代碼是否可以修改內部錯誤狀態。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>需求

**標題:** 非同步.h

**命名空間：** Microsoft::WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a>非同步基礎::非同步基礎

初始化 `AsyncBase` 類別的執行個體。

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a>非同步基礎::取消

取消非同步操作。

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>傳回值

默認情況下,始終返回S_OK。

### <a name="remarks"></a>備註

`Cancel()`是`IAsyncInfo::Cancel`的 默認實現,不執行實際工作。 要實際取消異步操作,請重寫`OnCancel()`純虛擬方法。

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a>非同步基礎::檢查有效狀態的委託呼叫

測試是否可以在當前異步狀態下修改委託屬性。

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>傳回值

S_OK是否可以修改委託屬性;如果可以修改委託屬性,則否則,E_ILLEGAL_METHOD_CALL。

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a>非同步基礎::檢查有效狀態結果呼叫

測試非同步操作的結果是否可以在當前異步狀態下收集。

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>傳回值

S_OK是否可以收集結果;否則,E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseclose"></a><a name="close"></a>非同步基礎:關閉

關閉非同步操作。

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>傳回值

如果操作關閉或已關閉,S_OK;否則,E_ILLEGAL_STATE_CHANGE。

### <a name="remarks"></a>備註

`Close()`是`IAsyncInfo::Close`的 默認實現,不執行實際工作。 要實際關閉非同步操作,重寫`OnClose()`純虛擬方法。

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a>非同步的基礎:繼續同步操作

確定非同步操作是繼續處理還是應停止。

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>傳回值

如果非同步操作的當前狀態*已啟動*,則**為 true,** 這意味著該操作應繼續。 否則 **,false**,這意味著操作應停止。

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a>非同步基礎::當前狀態

檢索當前異步操作的狀態。

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>參數

*狀態*<br/>
此操作儲存當前狀態的位置。

### <a name="remarks"></a>備註

此操作是線程安全的。

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a>非同步基礎::錯誤代碼

檢索當前非同步操作的錯誤代碼。

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>參數

*error*<br/>
此操作儲存目前的錯誤代碼的位置。

### <a name="remarks"></a>備註

此操作是線程安全的。

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a>非同步基礎::火完成

調用完成事件處理程式,或重置內部進度委託。

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>備註

第一個版本`FireCompletion()`重置內部進度委託變數。 如果非同步操作完成,第二個版本將調用完成事件處理程式。

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a>非同步基礎::火進度

調用當前進度事件處理程式。

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>參數

*精 氨 酸*<br/>
要調用的事件處理程式方法。

### <a name="remarks"></a>備註

`ProgressTraits`衍生自[阿格格瑟斯說明器結構](argtraitshelper-structure.md)。

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a>非同步基礎::get_ErrorCode

檢索當前非同步操作的錯誤代碼。

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>參數

*errorCode*<br/>
儲存目前的錯誤代碼的位置。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,如果關閉當前異步操作,則E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseget_id"></a><a name="get-id"></a>非同步基礎::get_Id

檢索異步操作的句柄。

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>參數

*id*<br/>
要存儲句柄的位置。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,E_ILLEGAL_METHOD_CALL。

### <a name="remarks"></a>備註

這個方法會實作 `IAsyncInfo::get_Id`。

## <a name="asyncbaseget_status"></a><a name="get-status"></a>非同步基礎::get_Status

檢索指示異步操作狀態的值。

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>參數

*狀態*<br/>
要存儲狀態的位置。 有關詳細資訊,請參閱`Windows::Foundation::AsyncStatus`枚舉。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,E_ILLEGAL_METHOD_CALL。

### <a name="remarks"></a>備註

這個方法會實作 `IAsyncInfo::get_Status`。

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a>非同步基礎::完成

將目前完成事件處理程式的位址複製到指定的變數。

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>參數

*完成漢德勒*<br/>
儲存目前完成事件處理程式位址的位置。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,E_ILLEGAL_METHOD_CALL。

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a>非同步基礎::取得進度

將當前進度事件處理程式的位址複製到指定的變數。

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>參數

*進度處理常式*<br/>
儲存目前的進度事件處理程式位址的位置。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a>非同步基礎::開啟取消

在派生類中重寫時,將取消非同步操作。

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a>非同步基礎:關閉

在派生類中重寫時,將關閉非同步操作。

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a>非同步基礎::開始

在派生類中重寫時,啟動非同步操作。

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a>非同步基礎::put_Id

設置非同步操作的句柄。

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>參數

*id*<br/>
非零句柄。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,E_INVALIDARG或E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a>非同步基礎::PutOnComplete

將完成事件處理程式的位址設置為指定值。

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>參數

*完成漢德勒*<br/>
將完成事件處理程式設置為的位址。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,E_ILLEGAL_METHOD_CALL。

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a>非同步基礎::P

將進度事件處理程式的位址設置為指定值。

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>參數

*進度處理常式*<br/>
將進度事件處理程式設置為的位址。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,E_ILLEGAL_METHOD_CALL。

## <a name="asyncbasestart"></a><a name="start"></a>非同步基礎::開始

啟動非同步操作。

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>傳回值

S_OK操作是否啟動或已啟動;如果操作已啟動,則否則,E_ILLEGAL_STATE_CHANGE。

### <a name="remarks"></a>備註

`Start()`是一種不受外部可見的受保護方法,因為異步操作在返回到調用方之前"熱啟動"。

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a>非同步基礎::嘗試過渡完成

指示當前非同步操作是否已完成。

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>傳回值

如果非同步操作已完成,**則為 true;** 否則,**假**。

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a>非同步基礎::嘗試轉換到錯誤

指示指定的錯誤代碼是否可以修改內部錯誤狀態。

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>參數

*error*<br/>
錯誤 HRESULT。

### <a name="return-value"></a>傳回值

如果內部錯誤狀態已更改,為 true;如果內部錯誤狀態已更改,**則為 true。** 否則,**假**。

### <a name="remarks"></a>備註

僅當錯誤狀態已設置為S_OK時,此操作才會修改錯誤狀態。 如果錯誤狀態已出錯、已取消、已完成或關閉,則此操作無效。
