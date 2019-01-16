---
title: AsyncStatusInternal 列舉
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: b38d58603eafeaa76c79873bbf375b4a3b405cdb
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336067"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal 列舉

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
enum AsyncStatusInternal;
```

## <a name="remarks"></a>備註

指定狀態的非同步作業的內部列舉型別之間的對應和`Windows::Foundation::AsyncStatus`列舉型別。

## <a name="members"></a>成員

`_Created`<br/>
相當於 `::Windows::Foundation::AsyncStatus::Created`。

`_Started`<br/>
相當於 `::Windows::Foundation::AsyncStatus::Started`。

`_Completed`<br/>
相當於 `::Windows::Foundation::AsyncStatus::Completed`。

`_Cancelled`<br/>
相當於 `::Windows::Foundation::AsyncStatus::Cancelled`。

`_Error`<br/>
相當於 `::Windows::Foundation::AsyncStatus::Error`。

## <a name="requirements"></a>需求

**標頭：** async.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)