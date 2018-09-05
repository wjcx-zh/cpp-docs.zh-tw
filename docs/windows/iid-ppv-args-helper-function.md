---
title: IID_PPV_ARGS_Helper 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
dev_langs:
- C++
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32970c9d30e1804071190ee5a57c42fd4b6334af
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677247"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper 函式

確認指定的引數的型別衍生自`IUnknown`介面。

> [!IMPORTANT]
> 此樣板特製化支援 WRL 結構，而且不是直接從您的程式碼使用。 使用[IID_PPV_ARGS](https://msdn.microsoft.com/library/windows/desktop/ee330727.aspx)改。

## <a name="syntax"></a>語法

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>參數

*T*  
引數的型別*pp*。

*前置處理*  
雙向間接指標。

## <a name="return-value"></a>傳回值

引數*pp*轉換成指標-至-a-指標**void**。

## <a name="remarks"></a>備註

如果，就會產生編譯時期錯誤的範本參數*T*不是衍生自`IUnknown`。

## <a name="requirements"></a>需求

**標頭：** client.h

