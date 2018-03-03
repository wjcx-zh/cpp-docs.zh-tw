---
title: "Asyncbase:: Put_id 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::put_Id
dev_langs:
- C++
helpviewer_keywords:
- put_Id method
ms.assetid: aebad85f-4774-42de-b625-a9cf5f65cb4e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 60135d69f6f3f8b73256fd65d89651351bd100e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbaseputid-method"></a>AsyncBase::put_Id 方法
設定非同步作業的控制代碼。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHOD(  
   put_Id  
)(const unsigned int id);  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 非零的控制代碼。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，E_INVALIDARG 或 E_ILLEGAL_METHOD_CALL。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)