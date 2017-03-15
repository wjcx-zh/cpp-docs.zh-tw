---
title: "improper_lock 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::improper_lock
dev_langs:
- C++
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
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
ms.openlocfilehash: 5a68573b8963fed90a4346fd421ef479c35dc247
ms.lasthandoff: 02/24/2017

---
# <a name="improperlock-class"></a>improper_lock 類別
這個類別描述以不當的方式取得鎖定時擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
class improper_lock : public std::exception;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[improper_lock 建構函式](#ctor)|多載。 建構 `improper_lock exception`。|  
  
## <a name="remarks"></a>備註  
 通常，當嘗試取得非可重新進入鎖定以遞迴方式，在相同的內容時，會擲回這個例外狀況。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `improper_lock`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namectora-improperlock"></a><a name="ctor"></a>improper_lock 

 建構 `improper_lock exception`。  
  
```
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [critical_section 類別](critical-section-class.md)   
 [reader_writer_lock 類別](reader-writer-lock-class.md)

