---
title: 'Comptrref:: Operator ！ = 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
dev_langs:
- C++
ms.assetid: ab3093cc-6fbd-4039-890a-6df1cde992b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4e2f0c432189dce1af9a255570dd259a90693591
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651287"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator!= 運算子
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   const Details::ComPtrRef<ComPtr<U>>& b  
);  
  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   decltype(__nullptr)  
);  
  
bool operator!=(  
   decltype(__nullptr),  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   void* b  
);  
  
bool operator!=(  
   void* b,  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
```  
  
### <a name="parameters"></a>參數  
 *a*  
 參考**ComPtrRef**物件。  
  
 *b*  
 另一個的參考**ComPtrRef**物件或匿名物件的指標 (`void*`)。  
  
## <a name="return-value"></a>傳回值  
 第一個運算子會產生 **，則為 true**如果物件是否不等於物件*b*否則**false**。  
  
 第二個和第三個運算子會產生 **，則為 true**如果物件是否不等於**nullptr**，則為**false**。  
  
 第四個和第五個運算子會產生 **，則為 true**如果物件是否不等於物件*b*，則為**false**。  
  
## <a name="remarks"></a>備註  
 指出兩個**ComPtrRef**物件是否不相等。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef 類別](../windows/comptrref-class.md)