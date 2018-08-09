---
title: 'Asyncbase:: Putonprogress 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnProgress
dev_langs:
- C++
helpviewer_keywords:
- PutOnProgress method
ms.assetid: 1f5f180e-eb5a-4afe-ac16-69dbf36f0383
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a99eee63496632b8f0918ee888e6a824424b757d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649886"
---
# <a name="asyncbaseputonprogress-method"></a>AsyncBase::PutOnProgress 方法
指定的值設定進度事件處理常式的位址。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDMETHOD(  
   PutOnProgress  
)(TProgress* progressHandler);  
```  
  
### <a name="parameters"></a>參數  
 *progressHandler*  
 設定進度事件處理常式的位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為 S_OK否則，E_ILLEGAL_METHOD_CALL。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)