---
title: 'Asyncbase:: Cancel 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Cancel
dev_langs:
- C++
helpviewer_keywords:
- Cancel method
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee338d4e90f94ed7cb7f9158235c66b72e9f2e52
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464742"
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
 根據預設，一律會傳回 S_OK。  
  
## <a name="remarks"></a>備註  
 `Cancel()` 預設實作`IAsyncInfo::Cancel`，並不執行任何實際工作。 若要實際取消非同步作業，請覆寫`OnCancel()`純虛擬方法。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)