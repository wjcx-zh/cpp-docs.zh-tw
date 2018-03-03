---
title: "Asyncbase:: Continueasyncoperation 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
dev_langs:
- C++
helpviewer_keywords:
- ContinueAsyncOperation method
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7e86c4857aab7c0e1a23dcd03695d906a3d9e5e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation 方法
決定是否應該繼續處理非同步作業，或應該中止。  
  
## <a name="syntax"></a>語法  
  
```  
inline bool ContinueAsyncOperation();  
```  
  
## <a name="return-value"></a>傳回值  
 `true`如果非同步作業的目前狀態是*啟動*，這表示作業應該繼續。 否則， `false`，這表示操作應該中止。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)