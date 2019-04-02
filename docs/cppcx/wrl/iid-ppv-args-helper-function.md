---
title: IID_PPV_ARGS_Helper 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 5ef4dd6c9db2d19e0c8a4143c5b4ed3f0ac75f6a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58783980"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper 函式

確認指定的引數的型別衍生自`IUnknown`介面。

> [!IMPORTANT]
> 此樣板特製化支援 WRL 結構，而且不是直接從您的程式碼使用。 使用[IID_PPV_ARGS](/windows/desktop/api/combaseapi/nf-combaseapi-iid_ppv_args)改。

## <a name="syntax"></a>語法

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>參數

*T*<br/>
引數的型別*pp*。

*pp*<br/>
雙向間接指標。

## <a name="return-value"></a>傳回值

引數*pp*轉換成指標-至-a-指標**void**。

## <a name="remarks"></a>備註

如果，就會產生編譯時期錯誤的範本參數*T*不是衍生自`IUnknown`。

## <a name="requirements"></a>需求

**標頭：** client.h

