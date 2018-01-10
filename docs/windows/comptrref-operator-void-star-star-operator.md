---
title: "Comptrref:: Operator void * * 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRef::operator void**
dev_langs: C++
helpviewer_keywords: operator void** operator
ms.assetid: f020045c-9de4-4392-8783-73f0fc0761c6
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a86f36f075dcee9688ee0eeca55e22a6eb7bb6fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="comptrrefoperator-void-operator"></a>ComPtrRef::operator void** 運算子
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
operator void**() const;  
```  
  
## <a name="remarks"></a>備註  
 刪除目前的 ComPtrRef 物件，會轉換至已做為指標--指標-將 ComPtrRef 物件所代表的介面指標`void`，然後傳回轉型指標。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>請參閱  
 [ComPtrRef 類別](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)