---
title: 'Hstring:: Operator ！ = 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
dev_langs:
- C++
ms.assetid: dcdd2aca-e7d6-4bf1-b2de-03efbb430a93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3fabc0dcbbc31a1707d1823fb1ec49a53aca6d3
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015871"
---
# <a name="hstringoperator-operator"></a>HString::Operator!= 運算子
表示兩個參數是否不相等。  
  
## <a name="syntax"></a>語法  
  
```cpp  
inline bool operator!=( const HString& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HStringReference& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HString& lhs,   
                        const HStringReference& rhs) throw()  
  
inline bool operator!=( const HSTRING& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HString& lhs,   
                        const HSTRING& rhs) throw()  
```  
  
### <a name="parameters"></a>參數  
 *lhs*  
 要比較的第一個參數。 *lhs*可以是**HString**或`HStringReference`物件或 HSTRING 控制代碼。  
  
 *rhs*  
 要比較的第二個參數。*rhs*可以是**HString**或`HStringReference`物件或 HSTRING 控制代碼。  
  
## <a name="return-value"></a>傳回值  
 **真**如果*lhs*並*rhs*參數不相等，否則**false**。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HString 類別](../windows/hstring-class.md)