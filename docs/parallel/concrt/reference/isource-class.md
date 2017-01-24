---
title: "ISource 類別 | Microsoft Docs"
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
  - "agents/concurrency::ISource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISource 類別"
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
caps.latest.revision: 20
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ISource 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`ISource` 類別是所有來源區塊的介面。  來源區塊會將訊息傳播至 `ITarget` 區塊。  
  
## 語法  
  
```  
template<  
   class _Type  
>  
class ISource;  
```  
  
#### 參數  
 `_Type`  
 來源區塊所產生之訊息內的承載的資料型別。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`source_type`|`_Type` 的型別別名。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[ISource::~ISource 解構函式](../Topic/ISource::~ISource%20Destructor.md)|終結 `ISource` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[ISource::accept 方法](../Topic/ISource::accept%20Method.md)|當在衍生類別中被覆寫時，接受這個 `ISource` 區塊所提供的訊息，將擁有權轉移至呼叫端。|  
|[ISource::acquire\_ref 方法](../Topic/ISource::acquire_ref%20Method.md)|在衍生類別中被覆寫時，取得這個 `ISource` 區塊的參考計數，以防止刪除。|  
|[ISource::consume 方法](../Topic/ISource::consume%20Method.md)|在衍生類別中被覆寫時，會消耗先前由此 `ISource` 區塊提供並順利保留在目標中的訊息，將擁有權轉移到呼叫端。|  
|[ISource::link\_target 方法](../Topic/ISource::link_target%20Method.md)|在衍生類別中被覆寫時，將目標區塊連結至這個 `ISource` 區塊。|  
|[ISource::release 方法](../Topic/ISource::release%20Method.md)|在衍生類別中被覆寫時，釋放前一個成功的訊息保留項目。|  
|[ISource::release\_ref 方法](../Topic/ISource::release_ref%20Method.md)|在衍生類別中被覆寫時，釋放這個 `ISource` 區塊的參考計數。|  
|[ISource::reserve 方法](../Topic/ISource::reserve%20Method.md)|在衍生類別中被覆寫，保留先前由這個 `ISource` 區塊所提供的訊息。|  
|[ISource::unlink\_target 方法](../Topic/ISource::unlink_target%20Method.md)|在衍生類別中被覆寫時，如果找到先前的連結，則將目標區塊與這個 `ISource` 區塊中斷連結。|  
|[ISource::unlink\_targets 方法](../Topic/ISource::unlink_targets%20Method.md)|在衍生類別中被覆寫時，將所有目標區塊與這個 `ISource` 區塊中斷連結。|  
  
## 備註  
 如需詳細資訊，請參閱 [非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 繼承階層架構  
 `ISource`  
  
## 需求  
 **標頭：** agents.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ITarget 類別](../../../parallel/concrt/reference/itarget-class.md)