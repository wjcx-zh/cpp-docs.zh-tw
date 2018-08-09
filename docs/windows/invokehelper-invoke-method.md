---
title: 'Invokehelper:: Invoke 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
dev_langs:
- C++
helpviewer_keywords:
- Invoke method
ms.assetid: 98618815-c30e-4699-b3dd-203c91b1bf3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 56f7f77284d855a2d9a737c8694efdd357d0a6fb
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011496"
---
# <a name="invokehelperinvoke-method"></a>InvokeHelper::Invoke 方法
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDMETHOD(  
   Invoke  
)();  
STDMETHOD(  
   Invoke  
)(typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
```  
  
### <a name="parameters"></a>參數  
 *arg1*  
 引數 1。  
  
 *Arg2*  
 引數 2。  
  
 *arg3*  
 引數 3。  
  
 *arg4*  
 引數 4。  
  
 *arg5*  
 引數 5。  
  
 *arg6*  
 引數 6。  
  
 *arg7*  
 引數 7。  
  
 *arg8*  
 引數 8。  
  
 *arg9*  
 引數 9。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為 S_OK否則，會描述錯誤的 HRESULT。  
  
## <a name="remarks"></a>備註  
 會呼叫其簽章包含指定的引數的事件處理常式。  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [InvokeHelper 結構](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)