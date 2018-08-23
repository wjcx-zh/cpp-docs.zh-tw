---
title: 'Asyncbase:: Putoncomplete 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnComplete
dev_langs:
- C++
helpviewer_keywords:
- PutOnComplete method
ms.assetid: 1c469ff9-b2df-4637-bf05-01a617043149
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c62119b87183fe6a60c0ed4d987cbd12788d8a0d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602682"
---
# <a name="asyncbaseputoncomplete-method"></a>AsyncBase::PutOnComplete 方法

指定的值設定完成事件處理常式的位址。

## <a name="syntax"></a>語法

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>參數

*completeHandler*  
設定完成事件處理常式的位址。

## <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，E_ILLEGAL_METHOD_CALL。

## <a name="requirements"></a>需求

**標頭：** async.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[AsyncBase 類別](../windows/asyncbase-class.md)