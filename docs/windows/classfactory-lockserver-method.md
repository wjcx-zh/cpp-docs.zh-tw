---
title: "Classfactory:: Lockserver 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ClassFactory::LockServer
dev_langs: C++
helpviewer_keywords: LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5f646f198d884e677b622a312cfdb6187802e1c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer 方法
遞增或遞減數目基礎物件，會追蹤目前 ClassFactory 物件。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
#### <a name="parameters"></a>參數  
 `fLock`  
 `true`要遞增的追蹤的物件數目。 `false`要遞減的追蹤的物件數目。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，E_FAIL。  
  
## <a name="remarks"></a>備註  
 ClassFactory 會追蹤的物件中的基礎執行個體[模組](../windows/module-class.md)類別。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [ClassFactory 類別](../windows/classfactory-class.md)