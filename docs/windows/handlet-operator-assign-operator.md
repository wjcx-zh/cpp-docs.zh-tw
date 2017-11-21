---
title: "Handlet:: Operator = 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
dev_langs: C++
helpviewer_keywords: operator= operator
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5c71e29fa31c89c030b74843a9d776923fed6789
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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