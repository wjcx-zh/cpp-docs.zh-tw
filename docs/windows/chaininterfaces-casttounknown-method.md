---
title: 'Chaininterfaces:: Casttounknown 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: a6a58555-e5b0-4773-aba0-959d9d362c6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96e7428e2263beb57eb73e024815000d61e75d5f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612553"
---
# <a name="chaininterfacescasttounknown-method"></a>ChainInterfaces::CastToUnknown 方法

將轉換的型別所定義的介面指標*I0*樣板參數的指標`IUnknown`。

## <a name="syntax"></a>語法

```cpp
__forceinline IUnknown* CastToUnknown();
```

## <a name="return-value"></a>傳回值

指標`IUnknown`。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[ChainInterfaces 結構](../windows/chaininterfaces-structure.md)