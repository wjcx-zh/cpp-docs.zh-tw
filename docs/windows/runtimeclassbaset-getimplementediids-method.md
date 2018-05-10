---
title: 'Runtimeclassbaset:: Getimplementediids 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- GetImplementedIIDS method
ms.assetid: adae54da-521d-4add-87f5-242fbd85f33b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9ea6ff871ef0ce886b393c948fc45accf3d8e245
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="runtimeclassbasetgetimplementediids-method"></a>RuntimeClassBaseT::GetImplementedIIDS 方法
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename T>  
__forceinline static HRESULT GetImplementedIIDS(  
   _In_ T* implements,  
   _Out_ ULONG *iidCount,  
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids  
);  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 `implements` 參數的類型。  
  
 `implements`  
 參數所指定型別的指標`T`。  
  
 `iidCount`  
 若要擷取的介面識別碼的數目上限。  
  
 `iids`  
 如果這項作業已順利完成，介面類型所實作的識別碼陣列`T`。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，描述錯誤的 HRESULT。  
  
## <a name="remarks"></a>備註  
 擷取介面指定類型所實作的識別碼陣列。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [RuntimeClassBaseT 結構](../windows/runtimeclassbaset-structure.md)