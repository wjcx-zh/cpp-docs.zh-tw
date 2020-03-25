---
title: AsyncStatusInternal 列舉
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: 0eadd1e3a287feecd36b00b231b42c31218352c1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214145"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal 列舉

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
enum AsyncStatusInternal;
```

## <a name="remarks"></a>備註

指定非同步作業狀態和 `Windows::Foundation::AsyncStatus` 列舉之內部列舉的對應。

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

**標頭：** async。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)
