---
title: WeakRef::operator&amp;運算子 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 900afb73-3801-4d08-9b41-2e6a62011ccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c8221b405618b1879f4e4c865115a227eb09857
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890100"
---
# <a name="weakrefoperatoramp-operator"></a>WeakRef::operator&amp;運算子
傳回表示目前 WeakRef 物件的 ComPtrRef 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&() throw()  
```  
  
## <a name="return-value"></a>傳回值  
 表示目前的 WeakRef 物件的 ComPtrRef 物件。  
  
## <a name="remarks"></a>備註  
 這是不是以用於您的程式碼中的內部協助程式運算子。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [WeakRef 類別](../windows/weakref-class.md)