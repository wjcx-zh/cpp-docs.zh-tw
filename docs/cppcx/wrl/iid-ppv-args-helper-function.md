---
title: IID_PPV_ARGS_Helper 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 6b1ab2e8e93fda194532fbc8d6f484aaa91249d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212965"
---
# <a name="iid_ppv_args_helper-function"></a>IID_PPV_ARGS_Helper 函式

驗證指定引數的類型衍生自 `IUnknown` 介面。

> [!IMPORTANT]
> 此範本特製化支援 WRL 基礎結構，但不適合直接從您的程式碼使用。 請改用[IID_PPV_ARGS](/windows/win32/api/combaseapi/nf-combaseapi-iid_ppv_args) 。

## <a name="syntax"></a>語法

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>參數

*T*<br/>
引數*pp*的類型。

*換*<br/>
雙向間接指標。

## <a name="return-value"></a>傳回值

引數*pp*轉換成指向指標的指標 **`void`** 。

## <a name="remarks"></a>備註

如果範本參數*T*不是衍生自，則會產生編譯時期錯誤 `IUnknown` 。

## <a name="requirements"></a>需求

**標頭：** client.h
