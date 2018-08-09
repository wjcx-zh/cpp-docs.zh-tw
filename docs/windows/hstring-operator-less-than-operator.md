---
title: 'Hstring:: Operator&lt;運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
dev_langs:
- C++
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1bdc6d54a6c9b60036d7434edec960715db304e2
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017678"
---
# <a name="hstringoperatorlt-operator"></a>Hstring:: Operator&lt;運算子
指出第一個參數是否小於第二個參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
inline bool operator<(  
    const HString& lhs,   
    const HString& rhs) throw()  
```  
  
### <a name="parameters"></a>參數  
 *lhs*  
 要比較的第一個參數。 *lhs*可以是參考**HString**。  
  
 *rhs*  
 要比較的第二個參數。 *rhs*可以是參考**HString**。  
  
## <a name="return-value"></a>傳回值  
 **真**如果*lhs*參數是小於*rhs*參數，否則**false**。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HString 類別](../windows/hstring-class.md)