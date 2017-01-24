---
title: "regex_error 類別 | Microsoft Docs"
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
  - "std::tr1::regex_error"
  - "regex_error"
  - "std.tr1.regex_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex_error 類別 [TR1]"
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
caps.latest.revision: 19
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# regex_error 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

回報錯誤的 basic\_regex 物件。  
  
## 語法  
  
```  
class regex_error  
    : public std::runtime_error {  
public:  
    explicit regex_error(regex_constants::error_code error);  
    regex_constants::error_code code() const;  
    };  
```  
  
## 備註  
 此類別描述為了回報建構或使用 `basic_regex` 物件時所發生的錯誤，所擲回的例外狀況物件。  
  
## 需求  
 **標頭：**\<regex\>  
  
 **命名空間：**std  
  
## 請參閱  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_error](../standard-library/regex-error-class.md)