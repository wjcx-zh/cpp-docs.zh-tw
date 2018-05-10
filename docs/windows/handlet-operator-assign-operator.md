---
title: 'Handlet:: Operator = 運算子 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a13e8eb7e74625e185b59816b5794b0390e95e3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="handletoperator-operator"></a>HandleT::operator= 運算子
將指定之 HandleT 物件的值移至目前 HandleT 物件。  
  
## <a name="syntax"></a>語法  
  
```  
HandleT& operator=(  
   _Inout_ HandleT&& h  
);  
```  
  
#### <a name="parameters"></a>參數  
 `h`  
 右值參考至控制代碼。  
  
## <a name="return-value"></a>傳回值  
 目前的 HandleT 物件的參考。  
  
## <a name="remarks"></a>備註  
 這項作業會導致無效的參數所指定的 HandleT 物件`h`。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HandleT 類別](../windows/handlet-class.md)