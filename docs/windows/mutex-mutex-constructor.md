---
title: "Mutex:: mutex 建構函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a07aeac0f8d139f71bdbe2473dc8eabf7e14ec2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex 建構函式
初始化 Mutex 類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
explicit Mutex(  
   HANDLE h  
);  
  
Mutex(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>參數  
 `h`  
 控制代碼或以 Mutex 物件的控制代碼，右值參考。  
  
## <a name="remarks"></a>備註  
 第一個建構函式初始化的 Mutex 物件，從指定的控制代碼。 第二個建構函式初始化從指定的控制代碼、 Mutex 物件，然後將 mutex 的擁有權移至目前的 Mutex 物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>請參閱
 [Mutex 類別](../windows/mutex-class1.md)