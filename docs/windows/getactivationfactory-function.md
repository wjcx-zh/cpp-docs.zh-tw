---
title: GetActivationFactory 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3fe0d03ead29362ea2926f6326557df2ba6a2cd9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649243"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory 函式
擷取的範本參數所指定之類型的啟用 factory。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<typename T>  
inline HRESULT GetActivationFactory(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory  
);  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 樣板參數，指定啟用 factory 的類型。  
  
 *activatableClassId*  
 啟用處理站可以產生的類別名稱。  
  
 *處理站*  
 這項作業完成時，參考型別的啟動處理站*T*。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為 S_OK否則，發生錯誤的 HRESULT，表示此作業失敗的原因。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** windows:: foundation  
  
## <a name="see-also"></a>另請參閱  
 [Windows::Foundation 命名空間](../windows/windows-foundation-namespace.md)