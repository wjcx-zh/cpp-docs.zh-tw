---
title: 'Chaininterfaces:: Fillarraywithiid 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: f1ce699c-dfb6-40a9-9ea0-e6703d3cf971
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 09e0dc3b9caf059bb8ecdce0468dfc118ce9ebfa
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594940"
---
# <a name="chaininterfacesfillarraywithiid-method"></a>ChainInterfaces::FillArrayWithIid 方法

介面 ID 所定義的存放區*I0*範本參數，以指定陣列中的介面識別碼指定的位置插入。

## <a name="syntax"></a>語法

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>參數

*index*  
到索引值的指標*iid*陣列。

*iid*  
介面識別碼的陣列。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[ChainInterfaces 結構](../windows/chaininterfaces-structure.md)