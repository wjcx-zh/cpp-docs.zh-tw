---
title: out_of_memory 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
dev_langs:
- C++
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b57e27647f61b551f8ea5c2770290e1ae9627014
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070914"
---
# <a name="outofmemory-class"></a>out_of_memory 類別
方法失敗，因為系統或裝置的記憶體不足時，會擲回例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class out_of_memory : public runtime_exception;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[out_of_memory 建構函式](#ctor)|初始化 `out_of_memory` 類別的新執行個體。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## <a name="requirements"></a>需求  
 **標頭：** amprt.h  
  
 **命名空間：** 並行  
## <a name="ctor"></a> out_of_memory 

 初始化類別的新執行個體。  
  
### <a name="syntax"></a>語法  
  
```  
explicit out_of_memory(  
    const char * _Message ) throw();  
  
out_of_memory () throw();  
```  
  
### <a name="parameters"></a>參數  
*訊息 （_m)*<br/>
錯誤的描述。  
  
### <a name="return-value"></a>傳回值  
 `out_of_memory` 類別的新執行個體。  
  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
