---
title: 'Chaininterfaces:: Cancastto 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8398f0bd4d9fdc786926782b13ebcac913a6a351
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612866"
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo 方法

指出指定的介面識別碼是否可轉換成每個非預設的範本參數所定義的特製化。

## <a name="syntax"></a>語法

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>參數

*riid*  
介面識別碼。

*ppv*  
已成功轉換的最後一個介面識別碼指標。

## <a name="return-value"></a>傳回值

**true**如果所有的 cast 作業成功，否則**false**。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[ChainInterfaces 結構](../windows/chaininterfaces-structure.md)