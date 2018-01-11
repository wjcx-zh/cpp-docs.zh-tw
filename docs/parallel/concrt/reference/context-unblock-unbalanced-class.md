---
title: "context_unblock_unbalanced 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
dev_langs: C++
helpviewer_keywords: context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44130ba1991a9e14340e44427e0bb80c5bac0a47
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="contextunblockunbalanced-class"></a>context_unblock_unbalanced 類別
這個類別描述時擲回的例外狀況呼叫`Block`和`Unblock`方法`Context`物件未正確配對。  
  
## <a name="syntax"></a>語法  
  
```  
class context_unblock_unbalanced : public std::exception;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[context_unblock_unbalanced](#ctor)|多載。 建構 `context_unblock_unbalanced` 物件。|  
  
## <a name="remarks"></a>備註  
 呼叫`Block`和`Unblock`方法`Context`物件必須一律正確配對。 並行執行階段可讓您按照任何順序，就可能發生的作業。 例如，呼叫 `Block` 之後可以呼叫 `Unblock`，反之亦然。 如果比方說，兩個呼叫會擲回這個例外狀況`Unblock`方法上，已進行資料列，`Context`物件已不會封鎖。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `context_unblock_unbalanced`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="ctor"></a>context_unblock_unbalanced 

 建構 `context_unblock_unbalanced` 物件。  
  
```  
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

 
context_unblock_unbalanced() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)
