---
title: "messages 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "messages"
  - "xlocmes/std::messages"
  - "std.messages"
  - "std::messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "messages 類別"
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# messages 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此樣板類別描述可以做為地區設定 facet 的物件，以便從特定地區設定的國際化訊息目錄擷取當地語系化訊息。  
  
 目前，雖然實作 messages 類別，但沒有訊息。  
  
## 語法  
  
```  
template <class CharType>  
   class messages : public messages_base;  
```  
  
#### 參數  
 `CharType`  
 程式內用於編碼地區設定字元的類型。  
  
## 備註  
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存的值儲存在唯一的正值 **識別碼**  
  
 這個 facet 基本上會開啟基底類別 messages\_base 所定義的訊息目錄，擷取所需的資訊，並關閉目錄。  
  
### 建構函式  
  
|||  
|-|-|  
|[訊息](../Topic/messages::messages.md)|訊息 facet 建構函式。|  
  
### Typedefs  
  
|||  
|-|-|  
|[char\_type](../Topic/messages::char_type.md)|用來顯示訊息的字元類型。|  
|[string\_type](../Topic/messages::string_type.md)|類型，描述包含 `basic_string` 類型字元的 `CharType` 類型字串。|  
  
### 成員函式  
  
|||  
|-|-|  
|[關閉](../Topic/messages::close.md)|關閉訊息目錄。|  
|[do\_close](../Topic/messages::do_close.md)|虛擬函式，呼叫以關閉訊息目錄。|  
|[do\_get](../Topic/messages::do_get.md)|虛擬函式，呼叫以擷取訊息目錄。|  
|[do\_open](../Topic/messages::do_open.md)|虛擬函式，呼叫以開啟訊息目錄。|  
|[取得](../Topic/messages::get.md)|擷取訊息目錄。|  
|[開啟](../Topic/messages::open.md)|開啟訊息目錄。|  
  
## 需求  
 **標頭：**\<locale\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<locale\>](../standard-library/locale.md)   
 [messages\_base 類別](../standard-library/messages-base-class.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)