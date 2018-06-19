---
title: 'Hstringreference:: Operator ！ = 運算子 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
dev_langs:
- C++
ms.assetid: 01ab6691-1fc7-4feb-85f0-fe795593a160
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ed2eeaceac23dc7a4efb17e2aba03cd9bc88eeb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876601"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator!= 運算子
指出兩個參數是否不相等。  
  
## <a name="syntax"></a>語法  
  
```cpp  
inline bool operator==(  
               const HStringReference& lhs,   
               const HSTRING& rhs) throw()  
  
inline bool operator!=(  
               const HStringReference& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator!=(  
               const HSTRING& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator!=(  
               const HStringReference& lhs,   
               const HSTRING& rhs) throw()  
  
```  
  
#### <a name="parameters"></a>參數  
 `lhs`  
 要比較的第一個參數。 `lhs` 可以是 HStringReference 物件或 HSTRING 控制代碼。  
  
 `rhs`  
 要比較的第二個參數。  `rhs` 可以是 HStringReference 物件或 HSTRING 控制代碼。  
  
## <a name="return-value"></a>傳回值  
 `true` 如果`lhs`和`rhs`參數不相等，否則`false`。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HStringReference 類別](../windows/hstringreference-class.md)