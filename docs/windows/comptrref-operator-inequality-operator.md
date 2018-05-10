---
title: 'Comptrref:: Operator ！ = 運算子 |Microsoft 文件'
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
ms.openlocfilehash: 3d5a6e7389215452177add30b587004c312aeae1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator!= 運算子
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
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
  
#### <a name="parameters"></a>參數  
 `a`  
 ComPtrRef 物件的參考。  
  
 `b`  
 另一個的 ComPtrRef 物件或匿名物件的指標的參考 (`void*`)。  
  
## <a name="return-value"></a>傳回值  
 第一個運算子會產生`true`如果物件`a`不等於物件`b`，否則`false`。  
  
 第二個和第三個運算子會產生`true`如果物件`a`不等於`nullptr`，否則`false`。  
  
 第四個和第五個運算子會產生`true`如果物件`a`不等於物件`b`，否則`false`。  
  
## <a name="remarks"></a>備註  
 指出兩個 ComPtrRef 物件是否不相等。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef 類別](../windows/comptrref-class.md)