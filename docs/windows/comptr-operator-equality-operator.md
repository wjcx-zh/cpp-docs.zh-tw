---
title: "Comptr:: Operator = = 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::operator==
dev_langs: C++
ms.assetid: 6a26e936-29d4-4b7d-b44a-7c575ad07509
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7eac03b462aeec3b30b00b2f065de645209178bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="comptroperator-operator"></a>ComPtr::operator== 運算子
表示兩個 ComPtr 物件是否相等。  
  
## <a name="syntax"></a>語法  
  
```cpp  
bool operator==(  
   const ComPtr<T>& a,  
   const ComPtr<U>& b  
);  
  
bool operator==(  
   const ComPtr<T>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
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
 第一個運算子會產生`true`如果物件`a`是否等於物件`b`，否則`false`。  
  
 第二個和第三個運算子會產生`true`如果物件`a`等於`nullptr`，否則`false`。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [Microsoft:: wrl 命名空間](../windows/microsoft-wrl-namespace.md)   
 [ComPtr 類別](../windows/comptr-class.md)