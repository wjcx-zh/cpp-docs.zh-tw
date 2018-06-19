---
title: 'Asyncbase:: Fireprogress 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::FireProgress
dev_langs:
- C++
helpviewer_keywords:
- FireProgress method
ms.assetid: 4512bef6-0ebc-4465-9b8a-4c9dfa82084c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c2c5aab609b597c3a9ff464b868ba831889deed
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863578"
---
# <a name="asyncbasefireprogress-method"></a>AsyncBase::FireProgress 方法
叫用目前的進度事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
void FireProgress(  
   const typename ProgressTraits::Arg2Type arg  
);  
```  
  
#### <a name="parameters"></a>參數  
 `arg`  
 要叫用的事件處理常式方法。  
  
## <a name="remarks"></a>備註  
 `ProgressTraits` 衍生自[ArgTraitsHelper 結構](../windows/argtraitshelper-structure.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)