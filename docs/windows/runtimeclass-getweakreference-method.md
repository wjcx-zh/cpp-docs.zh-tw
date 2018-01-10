---
title: "Runtimeclass:: Getweakreference 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass::GetWeakReference
dev_langs: C++
helpviewer_keywords: GetWeakReference method
ms.assetid: 26656ace-7f20-4364-87c9-4a75dd30912e
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ba87fe5097f9aff52b54770c1d438be2be425259
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclassgetweakreference-method"></a>RuntimeClass::GetWeakReference 方法
取得目前 RuntimeClass 物件的弱式參考物件的指標。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHOD(  
   GetWeakReference  
)(_Deref_out_ IWeakReference **weakReference);  
```  
  
#### <a name="parameters"></a>參數  
 `weakReference`  
 這項作業完成時，弱式參考物件的指標。  
  
## <a name="return-value"></a>傳回值  
 一律為 S_OK。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [RuntimeClass 類別](../windows/runtimeclass-class.md)