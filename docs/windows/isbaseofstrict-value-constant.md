---
title: 'Isbaseofstrict:: Value 常數 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
dev_langs:
- C++
helpviewer_keywords:
- value constant
ms.assetid: 4a0cdab0-ba03-482b-babf-eeec519ba687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eaaf0b410861f28cd5b339f75a73c594b1bcba45
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="isbaseofstrictvalue-constant"></a>IsBaseOfStrict::value 常數
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
static const bool value = __is_base_of(Base, Derived);  
```  
  
## <a name="remarks"></a>備註  
 指出是否會有一個類型的另一個基底。  
  
 `value` 是`true`如果型別`Base`基底類別之型別的`Derived`，否則就是`false`。  
  
## <a name="requirements"></a>需求  
 **標頭：** internal.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [IsBaseOfStrict 結構](../windows/isbaseofstrict-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)