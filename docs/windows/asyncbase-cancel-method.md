---
title: "Asyncbase:: Cancel 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Cancel
dev_langs:
- C++
helpviewer_keywords:
- Cancel method
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f23cae24cc3009108dd3bdadd7efc396459f0a60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbasecancel-method"></a>AsyncBase::Cancel 方法
取消非同步作業。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHOD(  
   Cancel  
)(void);  
```  
  
## <a name="return-value"></a>傳回值  
 根據預設，會一律傳回 S_OK。  
  
## <a name="remarks"></a>備註  
 Cancel （） 是 IAsyncInfo::Cancel 的預設實作，而且不執行任何實際工作。 若要實際取消非同步作業，覆寫 OnCancel() 純虛擬方法。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)