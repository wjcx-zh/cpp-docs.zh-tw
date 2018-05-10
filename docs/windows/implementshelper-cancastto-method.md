---
title: 'Implementshelper:: Cancastto 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 9ae6fa17-d0b1-4e31-9ae5-da6ae4026e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6de971f2de2421a2d7987dab30ba73fa2d225b15
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="implementshelpercancastto-method"></a>ImplementsHelper::CanCastTo 方法
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
  
HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
  
HRESULT CanCastTo(  
   _In_ const IID &iid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>參數  
 `riid`  
 參考介面識別碼。  
  
 `ppv`  
 如果這項作業成功時，所指定介面的指標`riid`或`iid`。  
  
 `iid`  
 參考介面識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。  
  
## <a name="remarks"></a>備註  
 取得指定的介面 ID 的指標  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [ImplementsHelper 結構](../windows/implementshelper-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)