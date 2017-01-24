---
title: "messages_byname 類別 | Microsoft Docs"
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
  - "messages_byname"
  - "std::messages_byname"
  - "std.messages_byname"
  - "xlocmes/std::messages_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "messages_byname 類別"
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
caps.latest.revision: 22
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# messages_byname 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

衍生的範本類別描述可以做為特定地區設定的訊息 Facet 的物件，可當地語系化訊息擷取。  
  
## 語法  
  
```  
template<class CharType>  
    class messages_byname : public messages<CharType> {  
public:  
    explicit messages_byname(  
        const char *_Locname,  
        size_t _Refs = 0  
    );  
    explicit messages_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );   
protected:  
    virtual ~messages_byname();  
};  
```  
  
#### 參數  
 `_Locname`  
 名為的地區設定。  
  
 `_Refs`  
 初始參考計數。  
  
## 備註  
 具名地區設定取決於其行為 `_Locname`。  每個建構函式並使用 [訊息](../Topic/messages::messages.md)\<CharType\>\(`_Refs`\) 的基礎物件。  
  
## 需求  
 **標題:** \<地區設定\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)