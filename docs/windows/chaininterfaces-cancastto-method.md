---
title: "Chaininterfaces:: Cancastto 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f614ec0eff2b448c8f20c88557f6228f85a770bd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo 方法
指出指定的介面識別碼可轉換成每個定義的非預設的範本參數特製化。  
  
## <a name="syntax"></a>語法  
  
```  
__forceinline bool CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>參數  
 `riid`  
 介面識別碼。  
  
 `ppv`  
 已成功轉換的最後一個介面 ID 的指標。  
  
## <a name="return-value"></a>傳回值  
 `true`如果成功轉換的所有作業;否則， `false`。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [ChainInterfaces 結構](../windows/chaininterfaces-structure.md)