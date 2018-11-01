---
title: DeferrableEventArgs 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::DeferrableEventArgs
- event/Microsoft::WRL::DeferrableEventArgs::GetDeferral
- event/Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished
helpviewer_keywords:
- Microsoft::WRL::DeferrableEventArgs class
- Microsoft::WRL::DeferrableEventArgs::GetDeferral method
- Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished method
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
ms.openlocfilehash: e00dcd5d1e62598e393d3798bd05d4bbc5633f72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471327"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs 類別

範本類別，用於延期的事件引數類型。

## <a name="syntax"></a>語法

```cpp
template <typename TEventArgsInterface, typename TEventArgsClass>
class DeferrableEventArgs : public TEventArgsInterface;
```

### <a name="parameters"></a>參數

*TEventArgsInterface*<br/>
宣告延期事件之引數的介面類別。

*TEventArgsClass*<br/>
此類別可實作*TEventArgsInterface*。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

名稱                                                         | 描述
------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------
[Deferrableeventargs:: Getdeferral](#getdeferral)             | 取得參考[延遲](http://go.microsoft.com/fwlink/p/?linkid=526520)代表延期的事件的物件。
[Deferrableeventargs:: Invokeallfinished](#invokeallfinished) | 呼叫此方法，表示已完成延期事件的所有處理。

## <a name="remarks"></a>備註

這個類別的執行個體會傳遞至延期事件的事件處理常式。 範本參數代表定義延期事件特定類型之事件引數詳細資料的介面，以及實作該介面的類別。

此類別會顯示為延期事件之事件處理常式的第一個引數。 您可以呼叫[GetDeferral](#getdeferral)方法來取得[延遲](http://go.microsoft.com/fwlink/p/?linkid=526520)從中中，您可以取得有關延期事件的所有資訊的物件。 完成事件處理之後，您應該在延期物件上呼叫 Complete。 您應該都會接著呼叫[InvokeAllFinished](#invokeallfinished)結尾的事件處理常式方法，以確保所有延期事件的完成都正確通訊。

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL

## <a name="getdeferral"></a>Deferrableeventargs:: Getdeferral

取得參考[延遲](http://go.microsoft.com/fwlink/p/?linkid=526520)代表延期的事件的物件。

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)
```

### <a name="parameters"></a>參數

*結果*<br/>
將參考的指標[延遲](http://go.microsoft.com/fwlink/p/?linkid=526520)物件呼叫完成時。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="invokeallfinished"></a>Deferrableeventargs:: Invokeallfinished

呼叫此方法，表示已完成延期事件的所有處理。

```cpp
void InvokeAllFinished()
```

### <a name="remarks"></a>備註

您應該呼叫這個方法之後的事件來源呼叫[InvokeAll](../windows/eventsource-invokeall-method.md)。 呼叫這個方法能避免其他延期，並在沒有採取任何延期時，強制執行完成處理常式。
