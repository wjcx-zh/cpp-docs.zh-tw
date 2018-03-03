---
title: "Runtimeclassbaset:: Asiid 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 90d7df8a-cf9e-4eef-8837-bc1a25f3fa1a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 482edbcabf368f68a720910717650be78ac11c62
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclassbasetasiid-method"></a>RuntimeClassBaseT::AsIID 方法
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
template<  
   typename T  
>  
__forceinline static HRESULT AsIID(  
   _In_ T* implements,  
   REFIID riid,  
   _Deref_out_ void **ppvObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 實作介面 ID 參數所指定的型別`riid`。  
  
 `implements`  
 範本參數所指定型別的變數`T`。  
  
 `riid`  
 要擷取的介面識別碼。  
  
 `ppvObject`  
 如果這項作業成功，指標至 a-指標的介面參數所指定`riid`。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，描述錯誤的 HRESULT。  
  
## <a name="remarks"></a>備註  
 擷取指定的介面 ID 的指標  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>請參閱  
 [RuntimeClassBaseT 結構](../windows/runtimeclassbaset-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)