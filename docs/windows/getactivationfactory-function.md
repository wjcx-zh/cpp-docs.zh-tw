---
title: GetActivationFactory 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd269b8c2e1c671944305d385064d60e8bf9b8a1
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="getactivationfactory-function"></a>GetActivationFactory 函式
擷取的範本參數所指定之類型的啟動 factory。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename T>  
inline HRESULT GetActivationFactory(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory  
);  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 樣板參數，指定啟動 factory 的類型。  
  
 `activatableClassId`  
 啟動處理站可以產生的類別名稱。  
  
 `factory`  
 這項作業完成時，啟動處理站類型的參考`T`。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，錯誤 HRESULT，表示此作業失敗的原因。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **Namespace:** Windows::Foundation  
  
## <a name="see-also"></a>另請參閱  
 [Windows::Foundation 命名空間](../windows/windows-foundation-namespace.md)