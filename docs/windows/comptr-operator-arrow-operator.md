---
title: "Comptr:: Operator-&gt;運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::operator->
dev_langs: C++
helpviewer_keywords: operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 28ac6f7dfc4e53e6aadc4fd082e10a0325124ee0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="comptroperator-gt-operator"></a>Comptr:: Operator-&gt;運算子
擷取目前範本參數所指定之類型的指標。  
  
## <a name="syntax"></a>語法  
  
```  
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;  
```  
  
## <a name="return-value"></a>傳回值  
 目前的範本型別名稱所指定之類型的指標。  
  
## <a name="remarks"></a>備註  
 這個 helper 函式中移除不必要使用 STDMETHOD 巨集所造成的負擔。 此函式會使得私人而非虛擬 IUnknown 型別。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ComPtr 類別](../windows/comptr-class.md)