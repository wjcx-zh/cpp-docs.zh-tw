---
title: "WeakRef::operator&amp;運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 900afb73-3801-4d08-9b41-2e6a62011ccd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 787712a857740afad539c0e44c450c6762aeb48f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [WeakRef 類別](../windows/weakref-class.md)