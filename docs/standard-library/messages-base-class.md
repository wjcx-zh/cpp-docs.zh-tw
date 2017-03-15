---
title: "messages_base 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.messages_base"
  - "messages_base"
  - "std::messages_base"
  - "locale/std::messages_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "messages_base 類別"
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# messages_base 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

基底類別會描述訊息目錄中的 `int` 型別。  
  
## 語法  
  
```  
struct messages_base : locale::facet {  
    typedef int catalog;  
    explicit messages_base(size_t _Refs = 0)  
};  
```  
  
## 備註  
 這個型別目錄是描述從 messages::[do\_open](../Topic/messages::do_open.md)的可能傳回值的型別為 `int` 的同義字。  
  
## 需求  
 **Header:** \<地區設定\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)