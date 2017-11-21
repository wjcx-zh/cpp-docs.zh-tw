---
title: "Asyncbase:: Getoncomplete 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::GetOnComplete
dev_langs: C++
helpviewer_keywords: GetOnComplete method
ms.assetid: f06ae02d-9a88-41d2-b749-bdc1a7ff8748
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3367832ec7dea157e5a0132b7ff10c5a4338bdd2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbasegetoncomplete-method"></a>AsyncBase::GetOnComplete 方法
將目前的完成事件處理常式的位址複製到指定的變數。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHOD(  
   GetOnComplete  
)(TComplete** completeHandler);  
```  
  
#### <a name="parameters"></a>參數  
 `completeHandler`  
 目前的完成事件處理常式的位址儲存位置。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，E_ILLEGAL_METHOD_CALL。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)