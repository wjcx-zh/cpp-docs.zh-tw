---
title: "Handlet:: Internalclose 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
dev_langs: C++
helpviewer_keywords: InternalClose method
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c91d3a6eb2c03b70ca50b28189e4ab4530a2e3bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose 方法
關閉目前的 HandleT 物件。  
  
## <a name="syntax"></a>語法  
  
```  
virtual bool InternalClose();  
```  
  
## <a name="return-value"></a>傳回值  
 `true`如果目前 HandleT 關閉順利啟動。否則， `false`。  
  
## <a name="remarks"></a>備註  
 InternalClose() 受到保護。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>請參閱  
 [HandleT 類別](../windows/handlet-class.md)