---
title: "ActivatableClass 巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
dev_langs:
- C++
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7043a3a9013f02048b34149dd113d2125dced6a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="activatableclass-macros"></a>ActivatableClass 巨集

擴展內部快取，其中包含可以建立指定類別的執行個體的 factory。

## <a name="syntax"></a>語法

```cpp
ActivatableClass(
   className
);

ActivatableClassWithFactory(
   className,
   factory
);

ActivatableClassWithFactoryEx(
   className,
   factory,
   serverName
);
```

### <a name="parameters"></a>參數

*類別名稱*  
若要建立類別的名稱。  

*處理站*  
將會建立指定類別的執行個體的 factory。

*伺服器名稱*  
指定模組中的處理站的子集名稱。

## <a name="remarks"></a>備註

請勿使用這些巨集與傳統 COM 除非您使用`#undef`指示詞，以確保**&#95; &#95;WRL_WINRT_STRICT #95; &#95;**會移除巨集定義。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>請參閱

[Module 類別](../windows/module-class.md)