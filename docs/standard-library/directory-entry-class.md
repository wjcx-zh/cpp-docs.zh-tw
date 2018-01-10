---
title: "directory_entry 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- filesystem/std::experimental::filesystem::directory_entry::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator=
- filesystem/std::experimental::filesystem::directory_entry::assign
- filesystem/std::experimental::filesystem::directory_entry::replace_filename
- filesystem/std::experimental::filesystem::directory_entry::path
- filesystem/std::experimental::filesystem::directory_entry::status
- filesystem/std::experimental::filesystem::directory_entry::symlink_status
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;
- filesystem/std::experimental::filesystem::directory_entry::operator==
- filesystem/std::experimental::filesystem::directory_entry::operator!=
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;=
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;=
dev_langs: C++
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::experimental::filesystem::directory_entry
- std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- std::experimental::filesystem::directory_entry::directory_entry
- std::experimental::filesystem::directory_entry::operator=
- std::experimental::filesystem::directory_entry::assign
- std::experimental::filesystem::directory_entry::replace_filename
- std::experimental::filesystem::directory_entry::path
- std::experimental::filesystem::directory_entry::status
- std::experimental::filesystem::directory_entry::symlink_status
- std::experimental::filesystem::directory_entry::operator&lt;
- std::experimental::filesystem::directory_entry::operator==
- std::experimental::filesystem::directory_entry::operator!=
- std::experimental::filesystem::directory_entry::operator&lt;=
- std::experimental::filesystem::directory_entry::operator&gt;
- std::experimental::filesystem::directory_entry::operator&gt;=
ms.workload: cplusplus
ms.openlocfilehash: 9f052d7f9991c88389bc2cb0c221a3c01d2fc529
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="directoryentry-class"></a>directory_entry 類別
描述 `*X` 所傳回的物件，其中 *X* 是 [directory_iterator](../standard-library/directory-iterator-class.md) 或 [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)。  
  
## <a name="syntax"></a>語法  
  
```  
class directory_entry;  
```  
  
## <a name="remarks"></a>備註  
 此類別會儲存 [path](../standard-library/path-class.md) 類型的物件。 預存的 `path` 可以是 [path 類別](../standard-library/path-class.md)的執行個體，或衍生自 `path` 之類型的執行個體。 它也會儲存兩個 [file_type](../standard-library/filesystem-enumerations.md#file_type) 值；一個代表已知的預存檔案名稱狀態，另一個則代表已知檔案名稱的符號連結狀態。  
  
 如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。  
  
## <a name="assign"></a>assign  
  
```  
void assign(const std::experimental::filesystem::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());
```  
  
 此成員函式會將 pval 指派給 mypath、將 stat 指派給 mystat，並將 symstat 指派給 mysymstat。  
  
## <a name="directoryentry"></a>directory_entry  
  
```  
directory_entry() = default;  
directory_entry(const directory_entry&) = default;  
directory_entry(directory_entry&&) noexcept = default;  
explicit directory_entry(const std::experimental::filesystem::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());
```  
  
 預設建構函式會如預期般運作。 第四個建構函式會將 mypath 初始化為 pval、將 mystat 初始化為 stat_arg，並將 mysymstat 初始化為 symstat_arg。  
  
## <a name="operator"></a>operator!=  
  
```  
bool operator!=(const directory_entry& right) const noexcept;  
```  
  
 此成員函式會傳回 !(*this == right)。  
  
## <a name="operator"></a>operator=  
  
```  
directory_entry& operator=(const directory_entry&) = default;  
directory_entry& operator=(directory_entry&&) noexcept = default;  
```  
  
 預設成員指派運算子會如預期般運作。  
  
## <a name="operator"></a>operator==  
  
```  
bool operator==(const directory_entry& right) const noexcept;  
```  
  
 此成員函式會傳回 mypath == right.mypath。  
  
## <a name="operatorlt"></a>運算子&lt;  
  
```  
bool operator<(const directory_entry& right) const noexcept;  
```  
  
 成員函式會傳回 mypath &lt; right.mypath。  
  
## <a name="operatorlt"></a>operator&lt;=  
  
```  
bool operator&lt;=(const directory_entry& right) const noexcept;  
```  
  
 此成員函式會傳回 !(right \< *this)。  
  
## <a name="operatorgt"></a>運算子&gt;  
  
```  
bool operator&gt;(const directory_entry& right) const noexcept;  
```  
  
 此成員函式會傳回 right \< *this。  
  
## <a name="operatorgt"></a>operator&gt;=  
  
```  
bool operator&gt;=(const directory_entry& right) const noexcept;  
```  
  
 成員函式會傳回 ！(* 這\<右)。  
  
## <a name="operator-const-pathtype"></a>operator const path_type&  
  
``` 
 operator const std::experimental::filesystem::path&() const; 
```  
  
 此成員運算子會傳回 mypath。  
  
## <a name="path"></a>路徑  
  
```  
const std::experimental::filesystem::path& path() const noexcept;  
```  
  
 此成員函式會傳回 mypath。  
  
## <a name="replacefilename"></a>replace_filename  
  
```  
void replace_filename(
    const std::experimental::filesystem::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());
```  
  
 此成員函式會以 mypath.parent_path() / pval 取代 mypath、以 stat_arg 取代 mystat，並以 symstat_arg 取代 mysymstat  
  
## <a name="status"></a>status  
  
```  
file_status status() const; 
file_status status(error_code& ec) const noexcept;  
```  
  
 這兩個成員函式都會傳回第一個可能修改的 mystat，如下所示：  
  
1.  如果為 status_known(mystat)，則不執行任何動作。  
  
2.  否則，如果為 !status_known(mysymstat) && !is_symlink(mysymstat)，則 mystat = mysymstat。  
  
## <a name="symlinkstatus"></a>symlink_status  
  
```  
file_status symlink_status() const; 
file_status symlink_status(error_code& ec) const noexcept;  
```  
  
 這兩個成員函式都會傳回第一個可能修改的 mysymstat，如下所示：如果為 status_known(mysymstat)，則不執行任何動作。 否則，mysymstat = symlink_status(mypval)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<實驗/檔案系統&gt;  
  
 **命名空間：**std::experimental::filesystem  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<檔案系統&gt;](../standard-library/filesystem.md)

