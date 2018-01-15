---
title: "Hstring:: Operator&lt;運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HString::operator<
dev_langs: C++
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4cbb21e34255d5350702d949792656bdf0a849a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hstringoperatorlt-operator"></a>Hstring:: Operator&lt;運算子
指出第一個參數是否小於第二個參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
inline bool operator<(  
    const HString& lhs,   
    const HString& rhs) throw()  
  
```  
  
#### <a name="parameters"></a>參數  
 `lhs`  
 要比較的第一個參數。 `lhs`可以是 HString 的參考。  
  
 `rhs`  
 要比較的第二個參數。 `rhs`可以是 HString 的參考。  
  
## <a name="return-value"></a>傳回值  
 `true`如果`lhs`參數小於`rhs`參數，否則`false`。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>請參閱  
 [HString 類別](../windows/hstring-class.md)