---
title: 'Weakreference:: Resolve 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::Resolve
dev_langs:
- C++
helpviewer_keywords:
- Resolve method
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dccdf7554f8d102230bedc18231feb74625d621b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890469"
---
# <a name="weakreferenceresolve-method"></a>WeakReference::Resolve 方法
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
  
STDMETHOD(Resolve)  
   (REFIID riid,   
   _Deref_out_opt_ IInspectable **ppvObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `riid`  
 介面識別碼。  
  
 `ppvObject`  
 這項作業完成時，一份目前的強式參考，如果強式參考計數不是零。  
  
## <a name="return-value"></a>傳回值  
  
-   如果這項作業成功，而且強式參考計數為零，即 S_OK。 `ppvObject` 參數設定為 `nullptr`。  
  
-   如果這項作業成功，而且強式參考計數不是零，即 S_OK。 `ppvObject`參數設定為強式參考。  
  
-   否則，失敗的 HRESULT，指出原因這項作業。  
  
## <a name="remarks"></a>備註  
 如果強式參考計數不是零，則您可以將目前強式參考值的指定的指標。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [WeakReference Class1](../windows/weakreference-class1.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)