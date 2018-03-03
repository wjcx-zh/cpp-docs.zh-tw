---
title: "AsyncStatusInternal 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
dev_langs:
- C++
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bd277fecb0bc63d5ee823af98df8aa298b285964
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal 列舉
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>備註  
 指定狀態的非同步作業的內部列舉型別之間的對應和**Windows::Foundation::AsyncStatus**列舉型別。  
  
## <a name="members"></a>成員  
 `_Created`  
 相當於:: Windows::Foundation::AsyncStatus:: 建立  
  
 `_Started`  
 相當於:: Windows::Foundation::AsyncStatus:: 已啟動  
  
 `_Completed`  
 相當於:: Windows::Foundation::AsyncStatus:: 完成  
  
 `_Cancelled`  
 相當於:: Windows::Foundation::AsyncStatus:: 已取消  
  
 `_Error`  
 相當於:: Windows::Foundation::AsyncStatus::Error  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)