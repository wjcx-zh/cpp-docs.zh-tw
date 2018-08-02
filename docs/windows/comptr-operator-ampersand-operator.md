---
title: 'Comptr:: Operator&amp;運算子 |Microsoft Docs'
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
ms.openlocfilehash: 0afff1699a4c7a3a14f07967cfb5ba5727ba0320
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461558"
---
# <a name="comptroperatoramp-operator"></a>Comptr:: Operator&amp;運算子
釋放與這個相關聯的介面**ComPtr**物件，並接著會擷取的地址**ComPtr**物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## <a name="return-value"></a>傳回值  
 目前的弱式參考**ComPtr**。  
  
## <a name="remarks"></a>備註  
 這個方法不同於[comptr:: Getaddressof](../windows/comptr-getaddressof-method.md) ，這個方法會釋放介面指標的參考。 使用`ComPtr::GetAddressOf`當您需要的介面指標的位址，但不是想要釋放該介面。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ComPtr 類別](../windows/comptr-class.md)