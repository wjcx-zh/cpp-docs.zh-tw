---
title: "invalid_link_target 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- invalid_link_target
- CONCRT/concurrency::invalid_link_target
- CONCRT/concurrency::invalid_link_target::invalid_link_target
dev_langs: C++
helpviewer_keywords: invalid_link_target class
ms.assetid: 33b64885-34d8-4d4e-a893-02e9f19c958e
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6335c51ef9edc97d1b44a6ed6bade6b653a87101
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="invalidlinktarget-class"></a>invalid_link_target 類別
這個類別描述呼叫傳訊區塊的 `link_target` 方法，但傳訊區塊無法連結至目標時所擲回的例外狀況。 這是由於超過傳訊區塊允許連結數目或嘗試將特定目標連結至相同的來源兩次所導致。  
  
## <a name="syntax"></a>語法  
  
```
class invalid_link_target : public std::exception;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[invalid_link_target](#ctor)|多載。 建構 `invalid_link_target` 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `invalid_link_target`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="ctor"></a>invalid_link_target 

 建構 `invalid_link_target` 物件。  
  
```
explicit _CRTIMP invalid_link_target(_In_z_ const char* _Message) throw();

invalid_link_target() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)



