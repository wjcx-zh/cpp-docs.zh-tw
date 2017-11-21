---
title: "invalid_compute_domain 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- invalid_compute_domain
- AMPRT/invalid_compute_domain
- AMPRT/Concurrency::invalid_compute_domain::invalid_compute_domain
dev_langs: C++
helpviewer_keywords: invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a6b41017563a7bd3c6e5ebfd3fc3752ea1e97c3a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="invalidcomputedomain-class"></a>invalid_compute_domain 類別
執行階段無法啟動一個核心使用在指定的計算網域時，會擲回的例外狀況[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)呼叫站台。  

  
## <a name="syntax"></a>語法  
  
```  
class invalid_compute_domain : public runtime_exception;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[invalid_compute_domain 建構函式](#ctor)|初始化 `invalid_compute_domain` 類別的新執行個體。|  

  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `runtime_exception`  
  
 `invalid_compute_domain`  
  
## <a name="requirements"></a>需求  
 **標頭：** amprt.h  
  
 **命名空間：** 並行  

## <a name="ctor"></a>invalid_compute_domain 

初始化類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
explicit invalid_compute_domain(  
    const char * _Message ) throw();  
  
invalid_compute_domain() throw();  
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述。  
  
### <a name="return-value"></a>傳回值  
 執行個體`invalid_compute_domain`類別  
    
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
