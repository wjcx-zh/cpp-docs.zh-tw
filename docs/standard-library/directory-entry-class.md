---
title: "directory_entry 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "filesystem/std::tr2::sys::directory_entry"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator const std::experimental::filesystem::v1::path &"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::directory_entry"
  - "std::experimental::filesystem::v1::directory_entry::directory_entry"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator="
  - "std::experimental::filesystem::v1::directory_entry::operator="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::assign"
  - "std::experimental::filesystem::v1::directory_entry::assign"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::replace_filename"
  - "std::experimental::filesystem::v1::directory_entry::replace_filename"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::path"
  - "std::experimental::filesystem::v1::directory_entry::path"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::status"
  - "std::experimental::filesystem::v1::directory_entry::status"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::symlink_status"
  - "std::experimental::filesystem::v1::directory_entry::symlink_status"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator<"
  - "std::experimental::filesystem::v1::directory_entry::operator<"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator=="
  - "std::experimental::filesystem::v1::directory_entry::operator=="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator!="
  - "std::experimental::filesystem::v1::directory_entry::operator!="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator<="
  - "std::experimental::filesystem::v1::directory_entry::operator<="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator>"
  - "std::experimental::filesystem::v1::directory_entry::operator>"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator>="
  - "std::experimental::filesystem::v1::directory_entry::operator>="
dev_langs: 
  - "C++"
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# directory_entry 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述 `*X` 所傳回的物件，其中 *X* 是 [directory\_iterator](../standard-library/directory-iterator-class.md) 或 [recursive\_directory\_iterator](../standard-library/recursive-directory-iterator-class.md)。  
  
## 語法  
  
```  
class directory_entry;  
```  
  
## 備註  
 此類別會儲存 [path 類別](../standard-library/path-class-cpp-standard-template-library.md)類型的物件。`path` 可以是[路徑](../standard-library/path-class-cpp-standard-template-library.md)或衍生自 `path` 的類型。 它也會儲存兩個 [file\_type](../Topic/file_type%20Enumeration.md) 值；一個代表已知的儲存檔案名稱狀態，另一個則代表已知的檔案名稱之符號連結狀態。  
  
 如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 \(C\+\+\)](../standard-library/file-system-navigation.md)。  
  
## assign  
  
```  
void assign(const PFX path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());  
```  
  
 此成員函式會將 pval 指派給 mypath、將 stat 指派給 mystat，並將 symstat 指派給 mysymstat。  
  
## directory\_entry  
  
```  
directory_entry() = default;  
directory_entry(const directory_entry&) = default;  
directory_entry(directory_entry&&) noexcept = default;  
explicit directory_entry(const PFX path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());  
```  
  
 預設建構函式會如預期般運作。 第四個建構函式會將 mypath 初始化為 pval、將 mystat 初始化為 stat\_arg，並將 mysymstat 初始化為 symstat\_arg。  
  
## operator\!\=  
  
```  
bool operator!=(const directory_entry& right) const noexcept;  
  
```  
  
 此成員函式會傳回 \!\(\*this \=\= right\)。  
  
## operator\=  
  
```  
directory_entry& operator=(const directory_entry&) = default;  
directory_entry& operator=(directory_entry&&) noexcept = default;  
  
```  
  
 預設成員指派運算子會如預期般運作。  
  
## operator\=\=  
  
```  
bool operator==(const directory_entry& right) const noexcept;  
```  
  
 此成員函式會傳回 mypath \=\= right.mypath。  
  
## operator\<  
  
```  
  
bool operator<(const directory_entry& right) const noexcept;  
  
```  
  
 此成員函式會傳回 mypath \< right.mypath。  
  
## operator\<\=  
  
```  
bool operator<=(const directory_entry& right) const noexcept;  
```  
  
 此成員函式會傳回 \!\(right \< \*this\)。  
  
## operator\>  
  
```  
bool operator>(const directory_entry& right) const noexcept;  
```  
  
 此成員函式會傳回 right \< \*this。  
  
## operator\>\=  
  
```  
bool operator>=(const directory_entry& right) const noexcept;  
  
```  
  
 此成員函式會傳回 \!\(\*this \< right\)。  
  
## operator const path\_type&  
  
```  
operator const path&() const; // retained  
```  
  
 此成員運算子會傳回 mypath。  
  
## path  
  
```  
const PFX path& path() const noexcept;  
```  
  
 此成員函式會傳回 mypath。  
  
## replace\_filename  
  
```  
void replace_filename(const PFX path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());  
```  
  
 此成員函式會以 mypath.parent\_path\(\) \/ pval 取代 mypath、以 stat\_arg 取代 mystat，並以 symstat\_arg 取代 mysymstat  
  
## status  
  
```  
file_status status() const;  
file_status status(  
    error_code& ec) const noexcept;  
Otherwise, mystat = status(mypval).  
  
```  
  
 這兩個成員函式都會傳回第一個可能修改的 mystat，如下所示：  
  
1.  如果為 status\_known\(mystat\)，則不執行任何動作。  
  
2.  否則，如果為 \!status\_known\(mysymstat\) && \!is\_symlink\(mysymstat\)，則 mystat \= mysymstat。  
  
## symlink\_status  
  
```  
file_status symlink_status() const;  
file_status symlink_status(  
    error_code& ec) const noexcept;  
```  
  
 這兩個成員函式都會傳回第一個可能修改的 mysymstat，如下所示：如果為 status\_known\(mysymstat\)，則不執行任何動作。 否則，mysymstat \= symlink\_status\(mypval\)。  
  
## 需求  
 **標頭：**filesystem  
  
 **命名空間：**std::tr2::sys  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem\>](../standard-library/filesystem.md)