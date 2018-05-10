---
title: AgileActivationFactory 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::AgileActivationFactory
dev_langs:
- C++
ms.assetid: fab98f32-bb93-4c0f-badb-49fbddb194b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9bcba7eeba0f63d67410526ee1920a79cab2eafa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="agileactivationfactory-class"></a>AgileActivationFactory 類別
表示 apartment 易記啟用 factory 實作[FtmBase](../windows/ftmbase-class.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <  
   typename I0 = Details::Nil,   
   typename I1 = Details::Nil,   
   typename I2 = Details::Nil,   
FactoryCacheFlags cacheFlagValue = FactoryCacheDefault>  
class AgileActivationFactory :   
   public ActivationFactory<Implements<FtmBase, I0>, I1, I2, cacheFlagValue>{};  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft:: wrl 命名空間](../windows/microsoft-wrl-namespace.md)   
 [ActivationFactory 類別](../windows/activationfactory-class.md)