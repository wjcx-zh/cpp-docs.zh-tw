---
title: 'Comptr:: Operator = 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fac3a845ea7c512f5a7ccffdabdf67ce26029ff8
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466159"
---
# <a name="comptroperator-operator"></a>ComPtr::operator= 運算子
將值指派給目前**ComPtr**。  
  
## <a name="syntax"></a>語法  
  
```  
WRL_NOTHROW ComPtr& operator=(  
   decltype(__nullptr)  
);  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ T *other  
);  
template <typename U>  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr &other  
);  
template<class U>  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr<U>& other  
);  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr &&other  
);  
template<class U>  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr<U>&& other  
);  
```  
  
#### <a name="parameters"></a>參數  
 *U*  
 類別中。  
  
 *other*  
 指標、 參考或右值參考類型或另一個**ComPtr**。  
  
## <a name="return-value"></a>傳回值  
 目前的參考**ComPtr**。  
  
## <a name="remarks"></a>備註  
 這個運算子的第一個版本會將空值指派給目前**ComPtr**。  
  
 在第二個版本中，如果指派的介面指標不是目前的相同**ComPtr**的介面指標，第二個介面指標指派給目前**ComPtr**。  
  
 在第三個版本中，指派的介面指標指派給目前**ComPtr**。  
  
 在第四個版本中，如果指派值的介面指標不是目前的相同**ComPtr**的介面指標，第二個介面指標指派給目前**ComPtr**。  
  
 第五個版本是複製運算子;參考**ComPtr**指派給目前**ComPtr**。  
  
 第六個版本是複製運算子使用移動語意;右值參考**ComPtr**如果任何型別是靜態的轉換，然後指派給目前**ComPtr**。  
  
 第七個版本是複製運算子使用移動語意;右值參考**ComPtr**型別的*U*會靜態然後轉換並指派給目前**ComPtr**。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ComPtr 類別](../windows/comptr-class.md)