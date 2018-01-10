---
title: "Asyncbase:: Fireprogress 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::FireProgress
dev_langs: C++
helpviewer_keywords: FireProgress method
ms.assetid: 4512bef6-0ebc-4465-9b8a-4c9dfa82084c
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 358a85f6ec0a451534684f2201caffefb1c1ad1b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
 `ProgressTraits`衍生自[ArgTraitsHelper 結構](../windows/argtraitshelper-structure.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)