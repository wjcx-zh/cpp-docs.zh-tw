---
title: 'Hstring:: Operator = 運算子 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
dev_langs:
- C++
ms.assetid: 8e68c1ff-bc57-4526-810e-af3c284b4e30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6fd1082beb6d84c5dded008e20683f7292cbc1e0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="hstringoperator-operator"></a>HString::Operator= 運算子
將另一個 HString 物件的值移至目前 HString 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HString& operator=(HString&& other) throw()  
```  
  
#### <a name="parameters"></a>參數  
 `other`  
 HString 現有的物件。  
  
## <a name="remarks"></a>備註  
 現有的值`other`物件會複製到目前的 HString 物件，然後`other`物件被終結。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HString 類別](../windows/hstring-class.md)