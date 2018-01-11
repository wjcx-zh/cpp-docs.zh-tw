---
title: "ActivateInstance 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
dev_langs: C++
helpviewer_keywords: ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 051eb51a4461d1b3f9ab180507022cdfa955f0ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="activateinstance-function"></a>ActivateInstance 函式
註冊並擷取在指定的類別識別碼中所定義之指定類型的執行個體  
  
## <a name="syntax"></a>語法  
  
```  
template<  
   typename T  
>  
inline HRESULT ActivateInstance(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance  
);  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要啟動類型。  
  
 `activatableClassId`  
 定義參數的類別識別碼的名稱`T`。  
  
 `instance`  
 這項作業完成時，執行個體的參考`T`。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，錯誤 HRESULT，表示錯誤的原因。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** windows:: foundation  
  
## <a name="see-also"></a>請參閱  
 [Windows::Foundation 命名空間](../windows/windows-foundation-namespace.md)