---
title: "ActivationFactoryCallback 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::ActivationFactoryCallback
dev_langs: C++
helpviewer_keywords: ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e88a6f9cb89746cd0380587789fbdd68f80d5e36
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback 函式
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(  
   HSTRING activationId,  
   IActivationFactory **ppFactory  
);  
```  
  
#### <a name="parameters"></a>參數  
 `activationId`  
 控制代碼指定的執行階段類別名稱的字串。  
  
 `ppFactory`  
 這項作業完成時，會對應至參數的啟用 factory `activationId`。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK，否則會是 HRESULT 指出失敗。 可能的失敗 Hresult 而 CLASS_E_CLASSNOTAVAILABLE E_INVALIDARG。  
  
## <a name="remarks"></a>備註  
 啟動處理站取得所指定的啟用識別碼。  
  
 Windows 執行階段呼叫這個要求由執行階段類別名稱指定物件的回呼函式。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)