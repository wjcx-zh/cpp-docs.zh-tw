---
title: "future_error 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "future/std::future_error"
dev_langs: 
  - "C++"
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# future_error 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述可以用型別方法擲回處理 [未來](../standard-library/future-class.md) 物件的例外狀況物件。  
  
## 語法  
  
```  
class future_error : public logic_error {  
public:  
   future_error(error_code code);  
   const error_code& code() const throw();  
   const char *what() const throw();  
};  
```  
  
## 需求  
 **標題:** future  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [logic\_error 類別](../standard-library/logic-error-class.md)   
 [error\_code 類別](../standard-library/error-code-class.md)