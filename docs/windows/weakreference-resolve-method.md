---
title: 'Weakreference:: Resolve 方法 |Microsoft Docs'
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
ms.openlocfilehash: 93df4ebf46b187cab63fbfaed2e273c55e7c0d84
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013245"
---
# <a name="weakreferenceresolve-method"></a>WeakReference::Resolve 方法
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDMETHOD(Resolve)  
   (REFIID riid,   
   _Deref_out_opt_ IInspectable **ppvObject  
);  
```  
  
### <a name="parameters"></a>參數  
 *riid*  
 介面識別碼。  
  
 *ppvObject*  
 這項作業完成時，一份目前的強式參考，如果強式參考計數為非零值。  
  
## <a name="return-value"></a>傳回值  
  
-   如果這項作業會成功，為 S_OK 和強式參考計數為零。 *PpvObject*參數設為**nullptr**。  
  
-   如果這項作業會成功，為 S_OK 和強式參考計數為非零值。 *PpvObject*參數設為強式參考。  
  
-   否則，指出原因的 HRESULT 這項作業失敗。  
  
## <a name="remarks"></a>備註  
 如果強式參考計數為非零值，請為目前的強式參考值設定指定的指標。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [WeakReference 類別 1](../windows/weakreference-class1.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)