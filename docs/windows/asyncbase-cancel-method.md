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
ms.openlocfilehash: 439a118bbea5adce4c306298e573bed85da26291
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641900"
---
# <a name="asyncbasecancel-method"></a>AsyncBase::Cancel 方法
取消非同步作業。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDMETHOD(  
   Cancel  
)(void);  
```  
  
## <a name="return-value"></a>傳回值  
 根據預設，一律會傳回 S_OK。  
  
## <a name="remarks"></a>備註  
 **Cancel**的預設實作`IAsyncInfo::Cancel`，並不執行任何實際工作。 若要實際取消非同步作業，請覆寫`OnCancel()`純虛擬方法。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)