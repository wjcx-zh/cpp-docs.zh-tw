---
title: Comptr::&amp;運算子 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0bfe8cf9091d888c33420f53f584ca5509d80527
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="comptroperatoramp-operator"></a>Comptr::&amp;運算子
釋放與此相關聯的介面`ComPtr`物件，並接著會擷取的位址`ComPtr`物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## <a name="return-value"></a>傳回值  
 目前的弱式參考`ComPtr`。  
  
## <a name="remarks"></a>備註  
 這個方法與[comptr:: Getaddressof](../windows/comptr-getaddressof-method.md) ，這個方法會釋放的介面指標的參考。 使用`ComPtr::GetAddressOf`當您需要的介面指標的位址，但不是想要釋放該介面。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ComPtr 類別](../windows/comptr-class.md)