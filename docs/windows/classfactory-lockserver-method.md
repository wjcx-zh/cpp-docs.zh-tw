---
title: 'Classfactory:: Lockserver 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e09a795688c7e2b31771126f9e4036ddfbd8e4f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
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
 `true` 要遞增的追蹤的物件數目。 `false` 要遞減的追蹤的物件數目。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，E_FAIL。  
  
## <a name="remarks"></a>備註  
 ClassFactory 會追蹤的物件中的基礎執行個體[模組](../windows/module-class.md)類別。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ClassFactory 類別](../windows/classfactory-class.md)