---
title: 'Comptr:: Operator-&gt;運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator->
dev_langs:
- C++
helpviewer_keywords:
- operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ff18dee2b8d951ab9233e92478eb967e4a02eb9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464294"
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
 此協助程式函式會移除不必要使用 STDMETHOD 巨集所造成的額外負荷。 這個功能可讓`IUnknown`型別**私人**而非**虛擬**。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ComPtr 類別](../windows/comptr-class.md)