---
title: 'Asyncbase:: Put_id 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::put_Id
dev_langs:
- C++
helpviewer_keywords:
- put_Id method
ms.assetid: aebad85f-4774-42de-b625-a9cf5f65cb4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 65d36c76ca05343084b709096d38014d802628c8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438999"
---
# <a name="asyncbaseputid-method"></a>AsyncBase::put_Id 方法

設定非同步作業的控制代碼。

## <a name="syntax"></a>語法

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>參數

*id*<br/>
非零的控制代碼。

## <a name="return-value"></a>傳回值

如果成功則為 S_OK否則 E_INVALIDARG 或 E_ILLEGAL_METHOD_CALL。

## <a name="requirements"></a>需求

**標頭：** async.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[AsyncBase 類別](../windows/asyncbase-class.md)