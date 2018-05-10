---
title: RaiseException 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
dev_langs:
- C++
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2af97ac13386db450318f4d1f384517a8dd77baf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="raiseexception-function"></a>RaiseException 函式
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
inline void __declspec(noreturn)   RaiseException(  
      HRESULT hr,   
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);  
```  
  
#### <a name="parameters"></a>參數  
 `hr`  
 引發; 例外狀況的例外狀況代碼也就是說，作業失敗的 HRESULT。  
  
 `dwExceptionFlags`  
 表示持續性例外狀況 （旗標值為零） 或 noncontinuable （旗標值為非零） 的例外狀況的旗標。 根據預設，例外狀況會是無法繼續。  
  
## <a name="remarks"></a>備註  
 引發的例外狀況，以呼叫的執行緒。  
  
 如需詳細資訊，請參閱 Windows **RaiseException**函式。  
  
## <a name="requirements"></a>需求  
 **標頭：** internal.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)