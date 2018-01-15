---
title: "Runtimeclass:: Getiids 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass::GetIids
dev_langs: C++
helpviewer_keywords: GetIids method
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e26101377aaf85cbae24e400557280d06d1402fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclassgetiids-method"></a>RuntimeClass::GetIids 方法
取得陣列，其中可以包含由目前 RuntimeClass 物件的識別碼實作的介面。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHOD(  
   GetIids  
)  
   (_Out_ ULONG *iidCount,   
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
#### <a name="parameters"></a>參數  
 `iidCount`  
 這項作業完成時，陣列中的項目總數`iids`。  
  
 `iids`  
 這項作業完成時，介面 Id 的陣列的指標。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，E_OUTOFMEMORY。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [RuntimeClass 類別](../windows/runtimeclass-class.md)