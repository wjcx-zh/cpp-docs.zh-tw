---
title: "&lt;filesystem&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::absolute
- FILESYSTEM/std::experimental::filesystem::canonical
- FILESYSTEM/std::experimental::filesystem::copy
- FILESYSTEM/std::experimental::filesystem::copy_file
- FILESYSTEM/std::experimental::filesystem::copy_symlink
- FILESYSTEM/std::experimental::filesystem::create_directories
- FILESYSTEM/std::experimental::filesystem::create_directory
- FILESYSTEM/std::experimental::filesystem::create_directory_symlink
- FILESYSTEM/std::experimental::filesystem::create_hard_link
- FILESYSTEM/std::experimental::filesystem::create_symlink
- FILESYSTEM/std::experimental::filesystem::current_path
- FILESYSTEM/std::experimental::filesystem::equivalent
- FILESYSTEM/std::experimental::filesystem::exists
- FILESYSTEM/std::experimental::filesystem::file_size
- FILESYSTEM/std::experimental::filesystem::hard_link_count
- FILESYSTEM/std::experimental::filesystem::hash_value
- FILESYSTEM/std::experimental::filesystem::is_block_file
- FILESYSTEM/std::experimental::filesystem::is_character_file
- FILESYSTEM/std::experimental::filesystem::is_directory
- FILESYSTEM/std::experimental::filesystem::is_empty
- FILESYSTEM/std::experimental::filesystem::is_fifo
- FILESYSTEM/std::experimental::filesystem::is_other
- FILESYSTEM/std::experimental::filesystem::is_regular_file
- FILESYSTEM/std::experimental::filesystem::is_socket
- FILESYSTEM/std::experimental::filesystem::is_symlink
- FILESYSTEM/std::experimental::filesystem::last_write_time
- FILESYSTEM/std::experimental::filesystem::permissions
- FILESYSTEM/std::experimental::filesystem::read_symlink
- FILESYSTEM/std::experimental::filesystem::remove
- FILESYSTEM/std::experimental::filesystem::remove_all
- FILESYSTEM/std::experimental::filesystem::rename
- FILESYSTEM/std::experimental::filesystem::resize_file
- FILESYSTEM/std::experimental::filesystem::space
- FILESYSTEM/std::experimental::filesystem::status
- FILESYSTEM/std::experimental::filesystem::status_known
- FILESYSTEM/std::experimental::filesystem::swap
- FILESYSTEM/std::experimental::filesystem::symlink_status
- FILESYSTEM/std::experimental::filesystem::system_complete
- FILESYSTEM/std::experimental::filesystem::temp_directory_path
- FILESYSTEM/std::experimental::filesystem::u8path
- filesystem/std::absolute
- filesystem/std::begin
- filesystem/std::canonical
- filesystem/std::copy
- filesystem/std::copy_file
- filesystem/std::copy_symlink
- filesystem/std::create_directories
- filesystem/std::create_directory
- filesystem/std::create_directory_symlink
- filesystem/std::create_hard_link
- filesystem/std::create_symlink
- filesystem/std::current_path
- filesystem/std::end
- filesystem/std::equivalent
- filesystem/std::exists
- filesystem/std::file_size
- filesystem/std::hard_link_count
- filesystem/std::hash_value
- filesystem/std::is_block_file
- filesystem/std::is_character_file
- filesystem/std::is_directory
- filesystem/std::is_empty
- filesystem/std::is_fifo
- filesystem/std::is_other
- filesystem/std::is_regular_file
- filesystem/std::is_socket
- filesystem/std::is_symlink
- filesystem/std::last_write_time
- filesystem/std::permissions
- filesystem/std::read_symlink
- filesystem/std::remove
- filesystem/std::remove_all
- filesystem/std::rename
- filesystem/std::resize_file
- filesystem/std::space
- filesystem/std::status
- filesystem/std::status_known
- filesystem/std::swap
- filesystem/std::symlink_status
- filesystem/std::system_complete
- filesystem/std::temp_directory_path
- filesystem/std::u8path
dev_langs:
- C++
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31a7a65ed759ec552e11f2eccc5d425c2b2b765d
ms.openlocfilehash: 253af6748b2d46ee1421604ed6f16fd97bf5a459
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt; 函式
[\<filesystem>](../standard-library/filesystem.md) 標頭中的這些免費函式會對路徑、檔案、符號連結、目錄和磁碟區執行修改及查詢作業。 如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。  
||||  
|-|-|-|  
|[absolute](#absolute)|[begin](#begin)|[canonical](#canonical)|
|[copy](#copy)|[copy_file](#copy_file)|[copy_symlink](#copy_symlink)|
|[create_directories](#create_directories)|[create_directory](#create_directory)|[create_directory_symlink](#create_directory_symlink)|
|[create_hard_link](#create_hard_link)|[create_symlink](#create_symlink)|[current_path](#current_path)|
|[end](#end)|[equivalent](#equivalent)|[exists](#exists)|
|[file_size](#file_size)|[hard_link_count](#hard_link_count)|[hash_value](#hash_value)|
|[is_block_file](#is_block_file)|[is_character_file](#is_character_file)|[is_directory](#is_directory)|
|[is_empty](#is_empty)|[is_fifo](#is_fifo)|[is_other](#is_other)|
|[is_regular_file](#is_regular_file)|[is_socket](#is_socket)|[is_symlink](#is_symlink)|
|[last_write_time](#last_write_time)|[permissions](#permissions)|[read_symlink](#read_symlink)|
|[remove](#remove)|[remove_all](#remove_all)|[rename](#rename)|
|[resize_file](#resize_file)|[space](#space)|[status](#status)|
|[status_known](#status_known)|[swap](#swap)|[symlink_status](#symlink_status)|
|[system_complete](#system_complete)|[temp_directory_path](#temp_directory_path)|[u8path](#u8path)|  


## <a name=""></a>  <a name="absolute"></a> absolute  
  
```  
path absolute(const path& pval, const path& base = current_path());
```  
  
 此函式會傳回與 `pval` 對應，但相對於路徑名稱 `base` 的絕對路徑名稱：  
  
1.  如果 pval.has_root_name() && pval.has_root_directory()，函式會傳回 pval。  
  
2.  如果 pval.has_root_name() && !pval.has_root_directory()，函式會傳回 pval.root_name() / absolute(base).root_directory() / absolute(base).relative_path() / pval.relative_path()。  
  
3.  如果 !pval.has_root_name() && pval.has_root_directory()，函式會傳回 absolute(base).root_name() / pval。  
  
4.  如果 !pval.has_root_name() && !pval.has_root_directory()，函式會傳回 absolute(base) / pval。  
  
## <a name="begin"></a>  begin  
  
```  
const directory_iterator& begin(const directory_iterator& iter) noexcept;  
const recursive_directory_iterator& 
    begin(const recursive_directory_iterator& iter) noexcept;  
```  
  
 兩個函式都會傳回 `iter`。  
  
## <a name="canonical"></a>  canonical  
  
```  
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```  
  
 所有函式都會形成絕對路徑名稱 pabs = absolute(pval, base) (或沒有基底參數多載的 pabs = absolute(pval))，然後在後續步驟中降低成標準格式：  
  
1.  每一個 is_symlink(X) 為 true 的路徑元件 X 都會被 read_symlink(X) 取代。  
  
2.  每一個路徑元件 . (點是目前的目錄，由上一個路徑元件所建立) 都已移除。  
  
3.  每一對路徑元件 X/.. (點點是父目錄，由上一個路徑元件所建立) 都已移除。  
  
 接著函式會傳回 pabs。  
  
## <a name="copy"></a>  copy  
  
```  
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;  
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;  
```  
  
 這些函式都可能複製或連結 `opts` 控制項下 `from` 到 `to` 的一或多個檔案，而針對不含 `opts` 參數的多載，系統會將其視為 copy_options::none。 `opts` 最多應該包含其中一個：  
  
-   skip_existing、overwrite_existing 或 update_existing  
  
-   copy_symlinks 或 skip_symlinks  
  
-   directories_only、create_symlinks 或 create_hard_links  
  
 函式會先判斷 `from` 的 file_status 值 f 和 `to` 的值 t：  
  
-   如果 opts & (copy_options::create_symlinks &#124; copy_options::skip_symlinks)，則方法是呼叫 symlink_status  
  
-   否則，呼叫狀態  
  
-   再則報告錯誤。  
  
 如果 !exists(f) &#124;&#124; equivalent(f, t) &#124;&#124; is_other(f) &#124;&#124; is_other(t) &#124;&#124; is_directory(f)&& is_regular_file(t)，它們就會回報錯誤 (不執行任何其他作業)。  
  
 否則，如果 is_symlink(f) 則：  
  
-   如果 options & copy_options::skip_symlinks 則不執行任何作業。  
  
-   否則，如果 !exists(t)&& options & copy_options::copy_symlinks 則 copy_symlink(from, to, opts)。  
  
-   再則報告錯誤。  
  
 否則，如果 is_regular_file(f) 則：  
  
-   如果 opts & copy_options::directories_only 則不執行任何作業。  
  
-   否則，如果 opts & copy_options::create_symlinks 則 create_symlink(to, from)。  
  
-   否則，如果 opts & copy_options::create_hard_links 則 create_hard_link(to, from)。  
  
-   否則，如果 is_directory(f) 則 copy_file(from, to / from.filename(), opts)。  
  
-   否則，copy_file(from, to, opts)。  
  
 否則，如果 s_directory(f) && (opts & copy_options::recursive &#124;&#124; !opts) 則：  
  
```cpp  
if (!exists(t))
{  // copy directory contents recursively  
    create_directory(to, from, ec);

    for (directory_iterator next(from), end; ec == error_code() && next != end; ++next)
    {
        copy(next->path(), to / next->path().filename(), opts, ec);
    }

}
```  
  
 否則，不執行任何作業。  
  
## <a name="opy_file"></a>  copy_file  
  
```  
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;  
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;  
```  
  
 這些函式都可能複製或連結 `opts` 控制項下 `from` 到 `to` 的檔案，而針對不含 `opts` 參數的多載，系統會將其視為 copy_options::none。 `opts` 最多應該包含 skip_existing、overwrite_existing 或 update_existing 的其中之一。  
  
 如果 exists\(to\) && \!\(opts & \(copy_options::skip_existing &#124; copy_options::overwrite_existing &#124; copy_options::update_existing\)\)，則回報檔案已存在的錯誤。  
  
 否則，如果 \!exists\(to\) &#124;&#124; opts & copy_options::overwrite_existing &#124;&#124; opts & copy_options::update_existing&& last_write_time\(to\) \< last_write_time\(from\) &#124;&#124; \!\(opts & \(copy_options::skip_existing &#124; copy_options::overwrite_existing &#124; copy_options:update_existing\)\)，則嘗試將檔案 from 的內容和屬性複製到檔案 to。 如果複製嘗試失敗，則報告錯誤。  
  
 如果複製嘗試成功，函式會傳回 true ，否則傳回 false。  
  
## <a name="copy_symlink "></a>  copy_symlink  
  
```  
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;  
```  
  
 如果 is_directory\(from\)，函式會呼叫 create_directory_symlink\(from, to\)。 否則，它會呼叫 create_symlink\(from, to\)。  
  
## <a name="create_directories"></a>  create_directories  
  
```  
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;  
```  
  
 若是 a\/b\/c 這類的路徑名稱，函式會視需要建立目錄 a 和 a\/b，以便有必要時可以建立目錄 a\/b\/c。 只有確實建立目錄 `pval` 時才會傳回 true。  
  
## <a name="create_directory"></a>  create_directory  
  
```  
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;  
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;  
```  
  
 函式會視需要建立目錄 `pval`。 只有確實建立目錄 `pval` 時才會傳回 true，在此情況下，它會從現有的檔案 `attr` 中複製權限，或對不含 `attr` 參數的多載使用 perms::all。  
  
## <a name="create_directory_symlink "></a>  create_directory_symlink  
  
```  
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;  
```  
  
 此函式會將連結建立為目錄 `to` 的符號連結。  
  
## <a name="create_hard_link"></a>  create_hard_link  
  
```  
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;  
```  
  
 此函式會將連結建立為目錄或檔案 `to` 的永久連結。  
  
## <a name="create_symlink "></a>  create_symlink  
  
```  
void create_symlink(const path& to,  const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;  
```  
  
 此函式會將 `link` 建立為檔案 `to` 的符號連結。  
  
## <a name="current_path"></a>  current_path  
  
```  
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;  
```  
  
 不含參數 `pval` 的函式會傳回目前目錄的路徑名稱。 其餘的函式會將目前的目錄設為 `pval`。  
  
## <a name="end"></a>  end  
  
```  
directory_iterator& end(const directory_iterator& iter) noexcept;  
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;  
```  
  
 第一個函式傳回 directory_iterator\(\)，第二個函式傳回 recursive_directory_iterator\(\)。  
  
## <a name="equivalent"></a>  equivalent  
  
```  
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;  
```  
  
 只有 `left` 和 `right` 指定相同的檔案系統實體，函式才會傳回 true。  
  
## <a name="exists"></a>  exists  
  
```  
bool exists(file_status stat) noexcept;  
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;  
```  
  
 第一個函式傳回 status_known && stat.type\(\) \!\= file_not_found。 第二個和第三個函式傳回 exists\(status\(pval\)\)。  
  
## <a name="file_size"></a>  file_size  
  
```  
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;  
```  
  
 如果 exists\(pval\) && is_regular_file\(pval\)，而且檔案大小可以判斷，函式就會傳回 `pval` 指定的檔案大小 (以位元組為單位)。 否則，函式會回報錯誤並傳回 uintmax_t\(\-1\)。  
  
## <a name="hard_link_count"></a>  hard_link_count  
  
```  
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;  
```  
  
 如果發生錯誤，函式會傳回 `pval` 的永久連結數目或 \-1。  
  
## <a name="hash_value"></a>  hash_value  
  
```  
size_t hash_value(const path& pval) noexcept;  
```  
  
 函式會傳回 pval.native\(\) 的雜湊值。  
  
## <a name="is_block_file"></a>  is_block_file  
  
```  
bool is_block_file(file_status stat) noexcept;  
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;  
```  
  
 第一個函式傳回 stat.type\(\) \=\= file_type::block。 其餘的函式傳回 is_block_file\(status\(pval\)\)。  
  
## <a name="is_character_file"></a>  is_character_file  
  
```   
bool is_character_file(file_status stat) noexcept;  
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;  
```  
  
 第一個函式傳回 stat.type\(\) \=\= file_type::character。 其餘的函式傳回 is_character_file\(status\(pval\)\)。  
  
## <a name="is_directory "></a>  is_directory  
  
```   
bool is_directory(file_status stat) noexcept;  
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;  
```  
  
 第一個函式傳回 stat.type\(\) \=\= file_type::directory。 其餘的函式傳回 is_directory_file\(status\(pval\)\)。  
  
## <a name="is_empty"></a>  is_empty  
  
```   
bool is_empty(file_status stat) noexcept;  
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;  
```  
  
 如果 is_directory\(pval\)，則函式傳回 directory_iterator\(pval\) \=\= directory_iterator\(\)；否則傳回 file_size\(pval\) \=\= 0。  
  
## <a name="is_fifo"></a>  is_fifo  
  
```  
bool is_fifo(file_status stat) noexcept;  
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;  
```  
  
 第一個函式傳回 stat.type\(\) \=\= file_type::fifo。 其餘的函式傳回 is_fifo\(status\(pval\)\)。  
  
## <a name="is_other"></a>  is_other  
  
```  
bool is_other(file_status stat) noexcept;  
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;  
```  
  
 第一個函式傳回 stat.type\(\) \=\= file_type::other。 其餘的函式傳回 is_other\(status\(pval\)\)。  
  
## <a name="s_regular_file"></a>  is_regular_file  
  
```   
bool is_regular_file(file_status stat) noexcept;  
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;  
```  
  
 第一個函式傳回 stat.type\(\) \=\= file_type::regular。 其餘的函式傳回 is_regular_file\(status\(pval\)\)。  
  
## <a name="is_socket"></a>  is_socket  
  
```   
bool is_socket(file_status stat) noexcept;  
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;  
```  
  
 第一個函式傳回 stat.type\(\) \=\= file_type::socket。 其餘的函式傳回 is_socket\(status\(pval\)\)。  
  
## <a name="is_symlink"></a>  is_symlink  
  
```   
bool is_symlink(file_status stat) noexcept;  
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;  
```  
  
 第一個函式傳回 stat.type\(\) \=\= file_type::symlink。 其餘的函式傳回 is_symlink\(status\(pval\)\)。  
  
## <a name="last_write_time"></a>  last_write_time  
  
```   
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;  
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;  
```  
  
 前兩個函式會傳回 `pval` 的上一次資料修改時間；如果發生錯誤，則傳回 file_time_type\(\-1\)。 最後兩個函式會將 `pval` 的上一次資料修改時間設為 new_time。  
  
## <a name="permissions"></a>  permissions  
  
```  
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;  
```  
  
 這些函式會將 `pval` 指定的路徑名稱權限遮罩設為 perms & \(perms::add_perms &#124; perms::remove_perms\) 控制項下的 mask & perms::mask。 遮罩最多應該包含 perms::add_perms 和 perms::remove_perms 的其中之一。  
  
 如果 mask & perms::add_perms，函式會將權限設為 status\(pval\).permissions\(\) &#124; mask & perms::mask。 否則，如果 mask & perms::remove_perms，函式會將權限設為 status\(pval\).permissions\(\) & ~\(mask & perms::mask\)。 否則，函式會將權限設為 mask & perms::mask。  
  
## <a name="read_symlink"></a>  read_symlink  
  
```  
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```  
  
 如果 \!is_symlink\(pval\)，函式會回報錯誤並傳回 path\(\)。 否則，函數會傳回包含符號連結的 `path` 類型物件。  
  
## <a name="remove"></a>  remove  
  
```  
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;  
```  
  
 只有 exists\(symlink_status\(pval\)\) 且成功移除檔案，函式才會傳回 true。 符號連結移除了自己本身，不是它指定的檔案。  
  
## <a name="remove_all"></a>  remove_all  
  
```  
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;  
```  
  
 如果 `pval` 是目錄，這些函式會以遞迴方式移除所有目錄項目，再移除項目本身。 否則，函式會呼叫 remove。 它們會傳回成功移除的所有元素計數。  
  
## <a name="rename"></a>  rename  
  
```  
void rename(const path& from,  const path& to);
void rename(const path& from,  const path& to, error_code& ec) noexcept;  
```  
  
 函式會將 `from` 重新命名為 `to`。 符號連結重新命名了自己本身，不是它指定的檔案。  
  
## <a name="resize_file"></a>  resize_file  
  
```  
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;  
```  
  
 函式變更了檔案的大小，因此 file_size\(pval\) \=\= size。  
  
## <a name="space"></a>  space  
  
```  
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;  
```  
  
 此函式會以 `space_info` 類型結構傳回 `pval` 指定的磁碟區相關資訊。 針對任何無法判斷的值，此結構會包含 uintmax_t\(\-1\)。  
  
## <a name="status"></a>  status  
  
```  
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;  
```  
  
 此函式會傳回與 `pval` 相關聯的路徑名稱狀態、檔案類型和權限。 系統並不會測試符號連結本身，但會測試其指定的檔案。  
  
## <a name="status_known"></a>  status_known  
  
```  
bool status_known(file_status stat) noexcept;  
```  
  
 函式傳回 stat.type\(\) \!\= file_type::none。  
  
## <a name="swap"></a>  swap  
  
```  
void swap(path& left, path& right) noexcept;  
```  
  
 函式會交換 `left` 和 `right` 的內容。  
  
## <a name="symlink_status"></a>  symlink_status  
  
```  
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;  
```  
  
 此函式會傳回與 `pval` 相關聯的路徑名稱符號連結狀態、檔案類型和權限。 函式的行為與 status\(pval\) 相同，只不過系統會測試符號連結本身，而不測試其指定的檔案。  
  
## <a name="system_complete"></a>  system_complete  
  
```  
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```  
  
 函式會傳回有必要納入考量的絕對路徑名稱，與其根名稱相關聯之目前的目錄。 \(至於 Posix，函式會傳回 absolute\(pval\)。\)  
  
## <a name="temp_directory_path"></a>  temp_directory_path  
  
```  
path temp_directory_path();
path temp_directory_path(error_code& ec);
```  
  
 函式會傳回適合包含暫存檔的目錄路徑名稱。  
  
## <a name="u8path"></a>  u8path  
  
```  
template <class Source>  
path u8path(const Source& source);

template <class InIt>  
path u8path(InIt first, InIt last);
```  
  
 第一個函式的行為與 path(source) 相同，第二個函式的行為與 path(first, last) 相同，不同之處在於每個案例中指定的來源會被視為一串 UTF-8 編碼的 char 元素，不論檔案系統為何。



