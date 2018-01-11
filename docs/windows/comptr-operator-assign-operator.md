---
title: "Comptr:: Operator = 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::operator=
dev_langs: C++
helpviewer_keywords: operator= operator
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 30f04bdfe7b508bf83e34992fefdcb10c58b4655
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="comptroperator-operator"></a>ComPtr::operator= 運算子
將值指派給目前的 ComPtr。  
  
## <a name="syntax"></a>語法  
  
```  
WRL_NOTHROW ComPtr& operator=(  
   decltype(__nullptr)  
);  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ T *other  
);  
template <  
   typename U  
>  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr &other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr<U>& other  
);  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr &&other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr<U>&& other  
);  
```  
  
#### <a name="parameters"></a>參數  
 `U`  
 類別。  
  
 `other`  
 型別或另一個的 ComPtr 指標、 參考或右值參考。  
  
## <a name="return-value"></a>傳回值  
 目前 ComPtr 的參考。  
  
## <a name="remarks"></a>備註  
 這個運算子的第一個版本會將空值指派給目前的 ComPtr。  
  
 在第二個版本中，如果指派的介面指標不是目前的 ComPtr 的介面指標，相同的第二個介面指標指派給目前的 ComPtr。  
  
 在第三個版本中，指派介面指標指派給目前的 ComPtr。  
  
 在第四個版本中，如果指派值的介面指標不是目前的 ComPtr 的介面指標，相同的第二個介面指標指派給目前的 ComPtr。  
  
 第五個版本是複製運算子;ComPtr 的參考會指派給目前的 ComPtr。  
  
 第六個版本是複製運算子使用移動語意。如果任何型別是靜態的轉換，然後指派給目前 ComPtr ComPtr 右值參考。  
  
 第七個版本是複製運算子使用移動語意。型別的 ComPtr 的右值參考`U`靜態然後轉型，且指派給目前的 ComPtr。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [ComPtr 類別](../windows/comptr-class.md)