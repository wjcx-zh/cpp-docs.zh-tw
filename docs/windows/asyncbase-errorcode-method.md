---
title: "Asyncbase:: Errorcode 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::ErrorCode
dev_langs: C++
helpviewer_keywords: ErrorCode method
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2aa8e137d1282f2a1e46a017192d213781e89090
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode 方法
擷取目前的非同步作業的錯誤碼。  
  
## <a name="syntax"></a>語法  
  
```  
inline void ErrorCode(  
   HRESULT *error  
);  
```  
  
#### <a name="parameters"></a>參數  
 `error`  
 這項作業對目前的錯誤程式碼的儲存位置。  
  
## <a name="remarks"></a>備註  
 這項作業是安全執行緒。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)