---
title: '&lt;filesystem&gt; 函式'
ms.date: 03/27/2019
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
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
helpviewer_keywords:
- std::experimental::filesystem::absolute
- std::experimental::filesystem::canonical
- std::experimental::filesystem::copy
- std::experimental::filesystem::copy_file
- std::experimental::filesystem::copy_symlink
- std::experimental::filesystem::create_directories
- std::experimental::filesystem::create_directory
- std::experimental::filesystem::create_directory_symlink
- std::experimental::filesystem::create_hard_link
- std::experimental::filesystem::create_symlink
- std::experimental::filesystem::current_path
- std::experimental::filesystem::equivalent
- std::experimental::filesystem::exists
- std::experimental::filesystem::file_size
- std::experimental::filesystem::hard_link_count
- std::experimental::filesystem::hash_value
- std::experimental::filesystem::is_block_file
- std::experimental::filesystem::is_character_file
- std::experimental::filesystem::is_directory
- std::experimental::filesystem::is_empty
- std::experimental::filesystem::is_fifo
- std::experimental::filesystem::is_other
- std::experimental::filesystem::is_regular_file
- std::experimental::filesystem::is_socket
- std::experimental::filesystem::is_symlink
- std::experimental::filesystem::last_write_time
- std::experimental::filesystem::permissions
- std::experimental::filesystem::read_symlink
- std::experimental::filesystem::remove
- std::experimental::filesystem::remove_all
- std::experimental::filesystem::rename
- std::experimental::filesystem::resize_file
- std::experimental::filesystem::space
- std::experimental::filesystem::status
- std::experimental::filesystem::status_known
- std::experimental::filesystem::swap
- std::experimental::filesystem::symlink_status
- std::experimental::filesystem::system_complete
- std::experimental::filesystem::temp_directory_path
- std::experimental::filesystem::u8path
ms.openlocfilehash: f1b48ed6f533d4ccb5f9ef5e6dbcbd6e5cc4f7a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332055"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt; 函式

檔系統>標頭中的這些自由函數對路徑、檔、符號連結、目錄和卷執行修改和查詢操作。 [ \<](../standard-library/filesystem.md) 有關詳細資訊和代碼範例,請參考[檔案系統導覽 (C++)](../standard-library/file-system-navigation.md)。

## <a name="absolute"></a><a name="absolute"></a>絕對

```cpp
path absolute(const path& pval, const path& base = current_path());
```

函數傳回與路徑名稱 :*pval*`base`

1. 如果`pval.has_root_name() && pval.has_root_directory()`函數傳回*pval*。

1. 如果`pval.has_root_name() && !pval.has_root_directory()``pval.root_name()` / `pval.relative_path()`函數 / 傳`absolute(base).relative_path()`回 。 / `absolute(base).root_directory()`

1. 如果`!pval.has_root_name() && pval.has_root_directory()`函數傳`absolute(base).root_name()` / 回*pval*。

1. 如果`!pval.has_root_name() && !pval.has_root_directory()`函數傳`absolute(base)` / 回*pval*。

## <a name="begin"></a><a name="begin"></a>開始

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

兩個函數都傳回*發代器*。

## <a name="canonical"></a><a name="canonical"></a>規範

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

這些函數都形成一個絕對路徑`pabs = absolute(pval, base)`名稱`pabs = absolute(pval)`( 或對於沒有基本參數的重載),然後按照以下步驟將它簡化為規範形式:

1. 為 true 的每個路徑元件`is_symlink(X)`都取代`read_symlink(X)`為 。**true**`X`

1. 將刪除每個`.`路徑元件(點是以前路徑元件建立的當前目錄)。

1. 將刪除每對路徑`X`/`..`元件(點點是以前路徑元件建立的父目錄)。

然後,函數傳`pabs`回 。

## <a name="copy"></a><a name="copy"></a>複製

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

這些函數都可能複製或連結一個或多個檔,*在從**到*控制*選擇*,`copy_options::none`這被視為 重載沒有*選擇*參數。 *選擇*要載入一個:

- `skip_existing`、`overwrite_existing` 或 `update_existing`

- `copy_symlinks` 或 `skip_symlinks`

- `directories_only`、`create_symlinks` 或 `create_hard_links`

函數首先確定*從*`t`和`f`*到*file_status的值。

- 如果`opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`,通過調用`symlink_status`

- 否則,通過調用`status`

- 再則報告錯誤。

如果`!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`,則它們報告錯誤(並且不執行任何其他操作)。

否則,如果`is_symlink(f)`這樣:

- 如果`options & copy_options::skip_symlinks`,則不執行任何操作。

- 否則,如果`!exists(t)&& options & copy_options::copy_symlinks``copy_symlink(from, to, opts)`, 則 。

- 否則,報告錯誤。

否則,如果`is_regular_file(f)`、

- 如果`opts & copy_options::directories_only`,則不執行任何操作。

- 否則,如果`opts & copy_options::create_symlinks``create_symlink(to, from)`, 則 。

- 否則,如果`opts & copy_options::create_hard_links``create_hard_link(to, from)`, 則 。

- 否則,如果`is_directory(f)``copy_file(from, to` / `from.filename(), opts)`, 則 。

- 否則為 `copy_file(from, to, opts)`。

否則,如果`is_directory(f) && (opts & copy_options::recursive || !opts)`、

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

## <a name="copy_file"></a><a name="copy_file"></a>copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

函數都可能*從**複製到**opts*控制下的`copy_options::none`檔,這被視為沒有*opts*參數的重載。 *選項*最多應包含的`skip_existing``overwrite_existing``update_existing`1 , 或 。

如果`exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`,則報告為該檔已存在的錯誤。

否則,如果`!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`,則嘗試將檔案的內容與屬性*從*複製到檔案*到*。 如果複製嘗試失敗，則報告錯誤。

如果試著複製並成功,則函數傳回**true,** 否則**為 false**。

## <a name="copy_symlink"></a><a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

如果`is_directory(from)`,`create_directory_symlink(from, to)`函數 呼叫 。 否則,它將呼叫`create_symlink(from, to)`。

## <a name="create_directories"></a><a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

對於路徑名稱(如\/\/b c),函數根據需要創建\/目錄 a 和 b,以便它可以\/\/根據需要創建目錄 b c。 僅當它實際上創建了目錄*pval*時,它才返回**true。**

## <a name="create_directory"></a><a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

函數根據需要創建目錄*pval。* 僅當它實際上創建了目錄*pval*時,它才返回 true,在這種情況下,它複製現有檔案*attr*的許可權,`perms::all`或者使用沒有*attr*參數的重載。

## <a name="create_directory_symlink"></a><a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

該函數創建連結作為指向*目錄的*符號連結。

## <a name="create_hard_link"></a><a name="create_hard_link"></a>create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

此函數建立連結作為指向目錄*或檔的硬*連結。

## <a name="create_symlink"></a><a name="create_symlink"></a>create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

該函數創建*鏈接*作為指向*檔的符號*連結。

## <a name="current_path"></a><a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

沒有參數*pval*的函數傳回目前的目錄的路徑名稱。 其餘函數將目前的目錄設定為*pval*。

## <a name="end"></a><a name="end"></a>結束

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

第一個函數`directory_iterator()`傳回,第二個函數傳回`recursive_directory_iterator()`

## <a name="equivalent"></a><a name="equivalent"></a>等效

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

僅當*左側*和*右側*選擇相同的文件系統實體時,函數才會返回**true。**

## <a name="exists"></a><a name="exists"></a>存在

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `status_known && stat.type() != file_not_found`。 第二個與第三個`exists(status(pval))`函數傳回 。

## <a name="file_size"></a><a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

如果`exists(pval) && is_regular_file(pval)`和檔大小可以確定,則函數返回*pval*選擇的檔案的大小(以位元組為單位)。 否則,它們會回報錯誤並`uintmax_t(-1)`傳回 。

## <a name="hard_link_count"></a><a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

函數返回*pval*的硬連結數\-,如果發生錯誤,則返回 1。

## <a name="hash_value"></a><a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

函數返回`pval.native()`的 哈希值。

## <a name="is_block_file"></a><a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::block`。 其餘函數傳`is_block_file(status(pval))`回 。

## <a name="is_character_file"></a><a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::character`。 其餘函數傳`is_character_file(status(pval))`回 。

## <a name="is_directory"></a><a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::directory`。 其餘函數傳`is_directory_file(status(pval))`回 。

## <a name="is_empty"></a><a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

如果`is_directory(pval)`,則`directory_iterator(pval) == directory_iterator()`函數 將返回 ;否則傳回`file_size(pval) == 0`。

## <a name="is_fifo"></a><a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::fifo`。 其餘函數傳`is_fifo(status(pval))`回 。

## <a name="is_other"></a><a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::other`。 其餘函數傳`is_other(status(pval))`回 。

## <a name="is_regular_file"></a><a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::regular`。 其餘函數傳`is_regular_file(status(pval))`回 。

## <a name="is_socket"></a><a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::socket`。 其餘函數傳`is_socket(status(pval))`回 。

## <a name="is_symlink"></a><a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::symlink`。 其餘函數傳`is_symlink(status(pval))`回 。

## <a name="last_write_time"></a><a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

前兩個函數傳回*pval*的最後一次資料`file_time_type(-1)`修改時間, 或者如果發生錯誤。 最後兩個函數將*pval*的最後一次資料修改時間設定為*new_time*。

## <a name="permissions"></a><a name="permissions"></a>權限

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

這些函數將*pval*選擇的路徑名稱的權`mask & perms::mask`限設定為`perms & (perms::add_perms | perms::remove_perms)`受控制的 。 *遮罩*最多應包含與`perms::add_perms` `perms::remove_perms` 。

如果`mask & perms::add_perms`,則函數將權限`status(pval).permissions() | mask & perms::mask`設定為 。 否則,如果`mask & perms::remove_perms`、函數將權限`status(pval).permissions() & ~(mask & perms::mask)`設定為 。 否則,函數將權限設定`mask & perms::mask`為 。

## <a name="proximate"></a><a name="proximate"></a>近似

```cpp
path proximate(const path& p, error_code& ec);
path proximate(const path& p, const path& base = current_path());
path proximate(const path& p, const path& base, error_code& ec);
```

## <a name="read_symlink"></a><a name="read_symlink"></a>read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

這些函數回報錯誤,如果`path()`傳`!is_symlink(pval)`回 。 否則，函數會傳回包含符號連結的 `path` 類型物件。

## <a name="relative"></a><a name="relative"></a>相對

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a><a name="remove"></a>刪除

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

僅當已成功刪除檔時`exists(symlink_status(pval))`,函數才會返回**true。** 符號連結本身被刪除,而不是它選擇的檔。

## <a name="remove_all"></a><a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

如果*pval*是目錄,則函數遞歸地刪除所有目錄條目,然後刪除條目本身。 否則,函數將呼叫`remove`。 它們會傳回成功移除的所有元素計數。

## <a name="rename"></a><a name="rename"></a>重新命名

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

函數*從*重新命名*到*。 符號連結本身被重命名,而不是它選擇的檔。

## <a name="resize_file"></a><a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

函數變更檔案的大小,以便`file_size(pval) == size`

## <a name="space"></a><a name="space"></a>空間

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

函數返回有關*pval*選擇的卷的資訊,在`space_info`類型的結構中。 結構包含`uintmax_t(-1)`任何無法確定的值。

## <a name="status"></a><a name="status"></a>地位

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

函數返回與*pval*關聯的路徑名稱狀態、檔案類型和許可權。 符號連結本身未測試,但會測試它選擇的檔。

## <a name="status_known"></a><a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

函數傳回`stat.type() != file_type::none`

## <a name="swap"></a><a name="swap"></a>交換

```cpp
void swap(path& left, path& right) noexcept;
```

函數交換*左右**的內容。*

## <a name="symlink_status"></a><a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

函數返回與*pval*關聯的路徑名稱符號連結狀態、檔案類型和許可權。 函數的運行情況與`status(pval)`symlink 本身測試不同,而不是它選擇的檔。

## <a name="system_complete"></a><a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

函式會傳回有必要納入考量的絕對路徑名稱，與其根名稱相關聯之目前的目錄。 \(對於 POSIX,函數`absolute(pval)`傳回 。\)

## <a name="temp_directory_path"></a><a name="temp_directory_path"></a>temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

函式會傳回適合包含暫存檔的目錄路徑名稱。

## <a name="u8path"></a><a name="u8path"></a>u8 路徑

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

第一個函數的表示與`path(source)`第二個函數相同的`path(first, last)`, 除了每個情況下所選的源被視為編碼為 UTF-8 的字元元素序列,無論檔案系統是什麼。

## <a name="weakly_canonical"></a><a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
