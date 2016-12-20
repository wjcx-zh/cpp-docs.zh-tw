---
title: "file_status 類別 | Microsoft Docs"
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
  - "filesystem/std::tr2::sys::file_status"
  - "filesystem/std::tr2::sys::file_status::perms"
  - "filesystem/std::tr2::sys::file_status::type"
dev_langs: 
  - "C++"
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
caps.latest.revision: 15
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# file_status 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包裝 [file\_type](../Topic/file_type%20Enumeration.md)。  
  
## 語法  
  
```  
class file_status;  
```  
  
## file\_status::file\_status  
  
```  
explicit file_status(file_type ftype = file_type::none,    perms mask = perms::unknown) noexcept;file_status(const file_status&) noexcept = default;file_status(file_status&&) noexcept = default;  
```  
  
## file\_status::operator\=  
  
```  
file_status& operator=(const file_status&) noexcept = default;  
file_status& operator=(file_status&&) nexcept = default;  
```  
  
 預設成員指派運算子會如預期般運作。  
  
## 類型  
  
```  
file_type type() const noexcept  
void type(file_type _Ftype) noexcept  
```  
  
 取得或設定 file\_type。  
  
## 權限  
  
```  
perms permissions() const noexcept  
void permissions(perms_Prms) noexcept   
```  
  
 取得或設定檔案權限。  
  
 使用 setter 將檔案設成唯讀或移除唯讀屬性。  
  
## 需求  
 **標頭：**filesystem  
  
 **命名空間：**std::tr2::sys  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [path 類別 \(C\+\+ 標準範本庫\)](../standard-library/path-class-cpp-standard-template-library.md)   
 [\<filesystem\>](../standard-library/filesystem.md)