---
title: 'Asyncbase:: Getoncomplete 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::GetOnComplete
dev_langs:
- C++
helpviewer_keywords:
- GetOnComplete method
ms.assetid: f06ae02d-9a88-41d2-b749-bdc1a7ff8748
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eab2a577d0c7b31f833a8dcc0208f9939b729ad9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607465"
---
# <a name="asyncbasegetoncomplete-method"></a>AsyncBase::GetOnComplete 方法

將目前的 「 完成 」 事件處理常式的位址複製到指定的變數中。

## <a name="syntax"></a>語法

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>參數

*completeHandler*  
目前的 「 完成 」 事件處理常式的位址儲存位置。

## <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，E_ILLEGAL_METHOD_CALL。

## <a name="requirements"></a>需求

**標頭：** async.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[AsyncBase 類別](../windows/asyncbase-class.md)