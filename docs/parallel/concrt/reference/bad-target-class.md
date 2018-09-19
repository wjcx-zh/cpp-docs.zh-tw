---
title: bad_target 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
dev_langs:
- C++
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12e035a27693fcad095cd83880aba99c37ba1c1f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027631"
---
# <a name="badtarget-class"></a>bad_target 類別
這個類別描述在傳訊區塊獲得目標的指標，但該目標對所執行的作業來說並不正確時，所擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
class bad_target : public std::exception;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[bad_target](#ctor)|多載。 建構 `bad_target` 物件。|  
  
## <a name="remarks"></a>備註  
 這個例外狀況通常會擲回的原因，例如做為目標，嘗試使用不同的目標保留的訊息，或釋出其並未持有的保留項目。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `bad_target`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="ctor"></a> bad_target 

 建構 `bad_target` 物件。  
  
```
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```  
  
### <a name="parameters"></a>參數  
*訊息 （_m)*<br/>
錯誤的描述性訊息。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)



