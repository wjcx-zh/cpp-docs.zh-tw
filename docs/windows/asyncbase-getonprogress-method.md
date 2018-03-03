---
title: "Asyncbase:: Getonprogress 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::GetOnProgress
dev_langs:
- C++
helpviewer_keywords:
- GetOnProgress method
ms.assetid: 286ddc9c-3e30-41a2-8e8b-e53d3fb0649d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8d83099b6842f9e758755e64aa8d7828a656aafb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbasegetonprogress-method"></a>AsyncBase::GetOnProgress 方法
將目前的進度事件處理常式的位址複製到指定的變數。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHOD(  
   GetOnProgress  
)(TProgress** progressHandler);  
```  
  
#### <a name="parameters"></a>參數  
 `progressHandler`  
 目前的進度事件處理常式的位址儲存位置。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，E_ILLEGAL_METHOD_CALL。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)