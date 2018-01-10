---
title: "Handlet:: Handlet 建構函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
dev_langs: C++
helpviewer_keywords: HandleT, constructor
ms.assetid: 4def6891-7e53-46f1-a197-a80e10744dd5
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b72db4fb44191340b71c8bff26018221650ae34b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [HandleT 類別](../windows/handlet-class.md)