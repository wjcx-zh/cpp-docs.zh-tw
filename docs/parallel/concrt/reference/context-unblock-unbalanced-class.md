---
title: "context_unblock_unbalanced 類別 | Microsoft Docs"
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
  - "concrt/concurrency::context_unblock_unbalanced"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "context_unblock_unbalanced 類別"
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# context_unblock_unbalanced 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別描述時擲回的例外狀況呼叫 `Block` 和 `Unblock` 方法 `Context` 物件未正確配對。  
  
## <a name="syntax"></a>語法  
  
```  
class context_unblock_unbalanced : public std::exception;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[context_unblock_unbalanced:: context_unblock_unbalanced 建構函式](#context_unblock_unbalanced__context_unblock_unbalanced_constructor)|多載。 建構 `context_unblock_unbalanced` 物件。|  
  
## <a name="remarks"></a>備註  
 呼叫 `Block` 和 `Unblock` 方法 `Context` 物件必須永遠正確配對。 並行執行階段可讓任何一種順序進行的作業。 例如，呼叫 `Block` 之後可以呼叫 `Unblock`，反之亦然。 這個例外狀況就會擲回，比方說，兩個呼叫 `Unblock` 方法對資料列，在 `Context` 未遭到封鎖的物件。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `context_unblock_unbalanced`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namecontextunblockunbalancedcontextunblockunbalancedconstructora-contextunblockunbalancedcontextunblockunbalanced-constructor"></a><a name="context_unblock_unbalanced__context_unblock_unbalanced_constructor"></a>  context_unblock_unbalanced:: context_unblock_unbalanced 建構函式  
 建構 `context_unblock_unbalanced` 物件。  
  
```  
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

 
context_unblock_unbalanced() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)
