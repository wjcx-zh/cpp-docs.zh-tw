---
title: "Comptr:: Comptr 建構函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr, constructor
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f8f6234bf2dff0dab801c982a585dc30e338bb7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="comptrcomptr-constructor"></a>ComPtr::ComPtr 建構函式
初始化 ComPtr 類別的新執行個體。 多載提供預設、複製、移動和轉換建構函式。  
  
## <a name="syntax"></a>語法  
  
```  
WRL_NOTHROW ComPtr();  
WRL_NOTHROW ComPtr(  
   decltype(__nullptr)  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr(  
   const ComPtr& other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   const ComPtr<U> &other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr &&other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr<U>&& other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
```  
  
#### <a name="parameters"></a>參數  
 `U`  
 `other` 參數的類型。  
  
 `other`  
 `U` 類型的物件。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 第一個建構函式是預設建構函式，哪一個隱含建立空的物件。 第二個建構函式指定[__nullptr](../windows/nullptr-cpp-component-extensions.md)，明確地建立空的物件。  
  
 第三個建構函式的指標所指定的物件從建立物件。  
  
 第四個和第五個建構函式是複製建構函式。 如果它轉換成目前的類型，第五個建構函式將物件複製。  
  
 第六個和第七個建構函式是移動建構函式。 第七個建構函式移動物件，如果它轉換成目前的類型。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [ComPtr 類別](../windows/comptr-class.md)