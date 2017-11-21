---
title: "Comptr:: Operator ！ = 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::operator!=
dev_langs: C++
ms.assetid: 63647240-dec7-4eb9-9272-96c07d01493c
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ce13c5dabf267be5d7c8a77a51d1450f182d226d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="comptroperator-operator"></a>ComPtr::operator!= 運算子
表示兩個 ComPtr 物件是否不相等。  
  
## <a name="syntax"></a>語法  
  
```cpp  
bool operator!=(  
   const ComPtr<T>& a,  
   const ComPtr<U>& b  
);  
  
bool operator!=(  
   const ComPtr<T>& a,  
   decltype(__nullptr)  
);  
  
bool operator!=(  
   decltype(__nullptr),  
   const ComPtr<T>& a  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `a`  
 ComPtr 物件的參考。  
  
 `b`  
 另一個 ComPtr 物件的參考。  
  
## <a name="return-value"></a>傳回值  
 第一個運算子會產生`true`如果物件`a`不等於物件`b`，否則`false`。  
  
 第二個和第三個運算子會產生`true`如果物件`a`不等於`nullptr`，否則`false`。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft:: wrl 命名空間](../windows/microsoft-wrl-namespace.md)   
 [ComPtr 類別](../windows/comptr-class.md)