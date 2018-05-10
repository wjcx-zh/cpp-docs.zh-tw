---
title: 'Handlet:: Handlet 建構函式 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
dev_langs:
- C++
helpviewer_keywords:
- HandleT, constructor
ms.assetid: 4def6891-7e53-46f1-a197-a80e10744dd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a0caad909803a0f73987f3e1132920b0948d8d1b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="handlethandlet-constructor"></a>HandleT::HandleT 建構函式
初始化 HandleT 類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
explicit HandleT(  
   typename HandleTraits::Type h =   
      HandleTraits::GetInvalidValue()  
);  
  
HandleT(  
   _Inout_ HandleT&& h  
);  
```  
  
#### <a name="parameters"></a>參數  
 `h`  
 控制代碼。  
  
## <a name="remarks"></a>備註  
 第一個建構函式初始化 HandleT 物件不是有效的控制代碼的物件。 第二個建構函式建立一個新 HandleT 從物件參數`h`。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HandleT 類別](../windows/handlet-class.md)