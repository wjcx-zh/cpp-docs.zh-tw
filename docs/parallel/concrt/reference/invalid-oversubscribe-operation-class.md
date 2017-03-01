---
title: "invalid_oversubscribe_operation 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::invalid_oversubscribe_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: becb02cfd6a052a019ee73e182804c63a286403e
ms.lasthandoff: 02/24/2017

---
# <a name="invalidoversubscribeoperation-class"></a>invalid_oversubscribe_operation 類別
這個類別描述將 `_BeginOversubscription` 參數設為 `false` 來呼叫 `Context::Oversubscribe` 方法，而不先將 `_BeginOversubscription` 參數設為 `true` 來呼叫 `Context::Oversubscribe` 方法時擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class invalid_oversubscribe_operation : public std::exception;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[invalid_oversubscribe_operation 建構函式](#ctor)|多載。 建構 `invalid_oversubscribe_operation` 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `invalid_oversubscribe_operation`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namectora-invalidoversubscribeoperation"></a><a name="ctor"></a>invalid_oversubscribe_operation 

 建構 `invalid_oversubscribe_operation` 物件。  
  
```  
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

 
invalid_oversubscribe_operation() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

