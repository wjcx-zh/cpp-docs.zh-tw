---
title: "ITarget 類別 | Microsoft Docs"
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
  - "agents/concurrency::ITarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ITarget 類別"
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
caps.latest.revision: 22
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ITarget 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`ITarget` 類別是所有目標區塊的介面。  目標區塊會使用 `ISource` 區塊提供給它們的訊息。  
  
## 語法  
  
```  
template<  
   class _Type  
>  
class ITarget;  
```  
  
#### 參數  
 `_Type`  
 目標區塊所接受之訊息內的承載的資料型別。  
  
## 成員  
  
### 公用 Typedefs  
  
|名稱|說明|  
|--------|--------|  
|`filter_method`|傳回 `bool` 值，以判斷是否應該會接受所提供的訊息在區塊所使用的任何方法簽章。|  
|`type`|`_Type` 的型別別名。|  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[ITarget::~ITarget 解構函式](../Topic/ITarget::~ITarget%20Destructor.md)|終結 `ITarget` 物件。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[ITarget::propagate 方法](../Topic/ITarget::propagate%20Method.md)|在衍生類別中被覆寫時，以非同步方式從來源區塊傳遞訊息到這個目標區塊。|  
|[ITarget::send 方法](../Topic/ITarget::send%20Method.md)|在衍生類別中被覆寫時，以同步方式將訊息傳遞到目標區塊。|  
|[ITarget::supports\_anonymous\_source 方法](../Topic/ITarget::supports_anonymous_source%20Method.md)|當在衍生類別中覆寫時，傳回 true 或 false 取決於訊息區塊會接受與它未連結的來源所提供的訊息。  如果要覆寫的方法會傳回 `true`，目標不可延後的所提供的訊息，因為已延後訊息耗用在其來源連結註冊後要求來源辨識。|  
  
### 受保護的方法  
  
|名稱|說明|  
|--------|--------|  
|[ITarget::link\_source 方法](../Topic/ITarget::link_source%20Method.md)|在衍生類別中被覆寫時，將指定來源區塊連結至這個 `ITarget` 區塊。|  
|[ITarget::unlink\_source 方法](../Topic/ITarget::unlink_source%20Method.md)|在衍生類別中被覆寫時，將指定來源區塊與這個 `ITarget` 區塊中斷連結。|  
|[ITarget::unlink\_sources 方法](../Topic/ITarget::unlink_sources%20Method.md)|在衍生類別中被覆寫時，將所有來源區塊與這個 `ITarget` 區塊中斷連結。|  
  
## 備註  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 繼承階層  
 `ITarget`  
  
## 需求  
 **標頭：** agents.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ISource 類別](../../../parallel/concrt/reference/isource-class.md)