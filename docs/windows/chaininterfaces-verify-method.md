---
title: "Chaininterfaces:: Verify 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d34d117091fd8807dfefda074e510910bf059560
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify 方法
確認每個介面定義的範本參數`I0`透過`I9`繼承自 IUnknown 和/或 IInspectable，而且`I0`繼承自`I1`透過`I9`。  
  
## <a name="syntax"></a>語法  
  
```  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## <a name="remarks"></a>備註  
 如果驗證作業失敗，`static_assert`發出描述失敗的錯誤訊息。  
  
## <a name="remarks"></a>備註  
 範本參數`I0`和`I1`是必要的與參數`I2`透過`I9`是選擇性的。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [ChainInterfaces 結構](../windows/chaininterfaces-structure.md)