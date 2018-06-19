---
title: 'Hstringreference:: Operator&lt;運算子 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
dev_langs:
- C++
ms.assetid: 55aa48e8-7c96-4123-9ebe-42b4cd8b9377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b486157fb42883af724f2356e7f85701e405035
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877289"
---
# <a name="hstringreferenceoperatorlt-operator"></a>Hstringreference:: Operator&lt;運算子
指出第一個參數是否小於第二個參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
inline bool operator<(  
    const HStringReference& lhs,   
    const HStringReference& rhs) throw()  
```  
  
#### <a name="parameters"></a>參數  
 `lhs`  
 要比較的第一個參數。 `lhs` 可以是 HStringReference 的參考。  
  
 `rhs`  
 要比較的第二個參數。  `rhs` 可以是 HStringReference 的參考。  
  
## <a name="return-value"></a>傳回值  
 `true` 如果`lhs`參數小於`rhs`參數，否則`false`。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HStringReference 類別](../windows/hstringreference-class.md)