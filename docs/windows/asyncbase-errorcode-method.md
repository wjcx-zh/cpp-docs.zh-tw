---
title: 'Asyncbase:: Errorcode 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- ErrorCode method
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7336824d04745440a1f6152ebacfed2afc62258e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602374"
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode 方法

擷取目前的非同步作業的錯誤碼。

## <a name="syntax"></a>語法

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>參數

*error*  
這項作業儲存目前的錯誤程式碼的位置。

## <a name="remarks"></a>備註

這項作業是安全執行緒。

## <a name="requirements"></a>需求

**標頭：** async.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[AsyncBase 類別](../windows/asyncbase-class.md)