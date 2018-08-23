---
title: 'Classfactory:: Addref 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method
ms.assetid: 5b091785-dea4-42b6-a502-0db5fc7a5a2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aeab6c448818d9d54ca96832a8c7875ebaa97091
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611355"
---
# <a name="classfactoryaddref-method"></a>ClassFactory::AddRef 方法

目前的參考計數會遞增**ClassFactory**物件。

## <a name="syntax"></a>語法

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

## <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[ClassFactory 類別](../windows/classfactory-class.md)