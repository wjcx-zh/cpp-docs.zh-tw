---
title: 'Asyncbase:: Continueasyncoperation 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
dev_langs:
- C++
helpviewer_keywords:
- ContinueAsyncOperation method
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b83d7a0bb5eadede42d2572d5ebc5a02a0fe9a0e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607181"
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation 方法

判斷是否應該繼續處理非同步作業，或應該停止。

## <a name="syntax"></a>語法

```cpp
inline bool ContinueAsyncOperation();
```

## <a name="return-value"></a>傳回值

**真**非同步作業的目前狀態是否*啟動*，這表示作業應該繼續。 否則，請**false**，這表示作業應該停止。

## <a name="requirements"></a>需求

**標頭：** async.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[AsyncBase 類別](../windows/asyncbase-class.md)