---
title: "uninitialized_object 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
dev_langs:
- C++
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a6c602ffa6cb444ce2245a655d47ffc9b548276
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="uninitializedobject-class"></a>uninitialized_object 類別
使用未初始化的物件時就會擲回例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class uninitialized_object : public runtime_exception;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[uninitialized_object 建構函式](#ctor)|初始化 `uninitialized_object` 類別的新執行個體。|  

  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `runtime_exception`  
  
 `uninitialized_object`  
  
## <a name="requirements"></a>需求  
 **標頭：** amprt.h  
  
 **命名空間：** 並行  
## <a name="uninitialized_object__ctor"></a> unsupported_feature 

建構 unsupported_feature 例外狀況的新執行個體。  
  
### <a name="syntax"></a>語法  
  
```  
explicit unsupported_feature(  
    const char * _Message ) throw();  
  
unsupported_feature() throw();  
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述。  
  
### <a name="return-value"></a>傳回值  
 `unsupported_feature` 物件。 

## <a name="see-also"></a>請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
