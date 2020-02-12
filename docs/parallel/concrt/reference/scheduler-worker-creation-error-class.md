---
title: scheduler_worker_creation_error 類別
ms.date: 11/04/2016
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
helpviewer_keywords:
- scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
ms.openlocfilehash: e7f2763d7244be9e5e5b006b31b97c08e213a4f2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142758"
---
# <a name="scheduler_worker_creation_error-class"></a>scheduler_worker_creation_error 類別

這個類別描述因為無法建立並行執行階段中的背景工作執行內容而擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[scheduler_worker_creation_error](#ctor)|已多載。 建構 `scheduler_worker_creation_error` 物件。|

## <a name="remarks"></a>備註

這個例外狀況通常是在從並行執行階段內呼叫作業系統建立執行內容失敗時擲回。 執行內容是指在並行執行階段的工作中執行的執行緒。 通常會從呼叫 Win32 方法 `GetLastError` 傳回的錯誤碼會轉換成 `HRESULT` 類型的值，並且可以使用基底類別方法 `get_error_code` 擷取。

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)

`scheduler_worker_creation_error`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>scheduler_worker_creation_error

建構 `scheduler_worker_creation_error` 物件。

```cpp
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

*_Hresult*<br/>
造成例外狀況之錯誤的 `HRESULT` 值。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
