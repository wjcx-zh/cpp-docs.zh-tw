---
title: "exception 類別 | Microsoft Docs"
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
  - "std.exception"
  - "exception"
  - "std::exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exception 類別"
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# exception 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可做為類別的 Standard C\+\+ 程式庫對於所有擲回的例外狀況是由某些運算式和基底類別。  
  
## 語法  
  
```  
class exception {  
public:  
    exception();  
    exception(const char * const &message);  
    exception(const char * const &message, int);  
    exception(const exception &right);  
    exception& operator=(const exception &right);  
    virtual ~exception();  
    virtual const char *what() const;  
};  
```  
  
## 備註  
 具體來說，這個基底類別是在 [\<stdexcept\>](../standard-library/stdexcept.md)中定義的標準例外狀況類別的根。  `what` 傳回的 C 字串值是由預設建構函式保持未指定，不過，可能是因為某些衍生類別的建構函式定義是由實作環境決定 C 字串。  成員函式都不會擲回任何例外狀況。  
  
 `int` 參數可讓您指定記憶體不應該配置。  `int` 的值會被忽略。  
  
> [!NOTE]
>  建構函式 `exception(const char * const &message)` 和 `exception(const char * const &message, int)` 是 Microsoft 擴充功能 Standard C\+\+ 程式庫。  
  
## 範例  
 以從 `exception` 類別繼承的使用標準例外狀況類別的範例，請參閱 [\<stdexcept\>](../standard-library/stdexcept.md)中定義的任何類別。  
  
## 需求  
 **標頭 :** \<exception\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)