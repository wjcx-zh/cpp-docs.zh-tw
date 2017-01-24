---
title: "filesystem_error 類別 | Microsoft Docs"
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
  - "filesystem/std::tr2::sys::filesystem_error"
dev_langs: 
  - "C++"
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
caps.latest.revision: 13
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# filesystem_error 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擲回所有例外狀況的基底類別，以報告低階系統溢位。  
  
## 語法  
  
```  
class filesystem_error    : public system_error;  
```  
  
## 備註  
 此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告 \<filesystem\> 的錯誤。 它會儲存 string 類型物件，這裡稱為 mymesg 主要是為了公開的目的。 它也會儲存兩個 path 類型物件，稱為 mypval1 和 mypval2。  
  
## filesystem\_error::filesystem\_error  
  
```  
filesystem_error(const string& what_arg, error_code ec);  
filesystem_error(const string& what_arg,  
    const path& pval1, error_code ec);  
filesystem_error(const string& what_arg,  
    const path& pval1, const path& pval2, error_code ec);  
```  
  
 第一個建構函式會從 what\_arg 和 ec 建構其訊息。 第二個建構函式也會從 pval1 建構其訊息，並存放在 mypval1。 第三個建構函式也會從 pval1 與 pval2 建構其訊息，並存放在 mypval1 和 mypval2 中。  
  
## filesystem\_error::path1  
  
```  
const path& path1() const noexcept;  
  
```  
  
 成員函式傳回 mypval1  
  
## filesystem\_error::path2  
  
```  
const path& path2() const noexcept;  
  
```  
  
 成員函式傳回 mypval2  
  
## filesystem\_error::what  
  
```  
const char *what() const noexcept;  
```  
  
 成員函式會傳回 NTBS 的指標，最好是由 runtime\_error::what\(\)、system\_error::what\(\)、mymesg、mypval1.native\_string\(\) 和 mypval2.native\_string\(\) 組成 。  
  
## 需求  
 **標頭：**filesystem  
  
 **命名空間：**std::tr2::sys  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [system\_error 類別](../standard-library/system-error-class.md)   
 [\<filesystem\>](../standard-library/filesystem.md)   
 [\<exception\>](../standard-library/exception.md)