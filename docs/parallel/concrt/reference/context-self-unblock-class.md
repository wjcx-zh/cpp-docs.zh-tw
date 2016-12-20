---
title: "context_self_unblock 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::context_self_unblock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "context_self_unblock 類別"
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# context_self_unblock 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別描述從同樣的內容呼叫 `Context` 物件的 `Unblock` 方法所擲回的例外狀況。 這會指出指定內容自行解除封鎖的嘗試。  
  
## <a name="syntax"></a>語法  
  
```  
class context_self_unblock : public std::exception;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[context_self_unblock:: context_self_unblock 建構函式](#context_self_unblock__context_self_unblock_constructor)|多載。 建構 `context_self_unblock` 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `context_self_unblock`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namecontextselfunblockcontextselfunblockconstructora-contextselfunblockcontextselfunblock-constructor"></a><a name="context_self_unblock__context_self_unblock_constructor"></a>  context_self_unblock:: context_self_unblock 建構函式  
 建構 `context_self_unblock` 物件。  
  
```  
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

 
context_self_unblock() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)
