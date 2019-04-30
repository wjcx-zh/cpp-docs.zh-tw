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
ms.openlocfilehash: 11a1857052dd7c242993e8a19afe26aae3c97c06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405101"
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

## <a name="absolute"></a> 絕對

```cpp
path absolute(const path& pval, const path& base = current_path());
```

此函數會傳回對應至的絕對路徑名稱*pval*相對於路徑名稱`base`:

1. 如果`pval.has_root_name() && pval.has_root_directory()`函式會傳回*pval*。

1. 如果`pval.has_root_name() && !pval.has_root_directory()`函式會傳回`pval.root_name()`  /  `absolute(base).root_directory()`  /  `absolute(base).relative_path()`  /  `pval.relative_path()`。

1. 如果`!pval.has_root_name() && pval.has_root_directory()`函式會傳回`absolute(base).root_name()`  /  *pval*。

1. 如果`!pval.has_root_name() && !pval.has_root_directory()`函式會傳回`absolute(base)`  /  *pval*。

## <a name="begin"></a>  begin

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

這兩個函式會傳回*iter*。

## <a name="canonical"></a>  canonical

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

函式都會形成絕對路徑名稱`pabs = absolute(pval, base)`(或`pabs = absolute(pval)`沒有基底參數多載)，然後將其降低成標準格式以下列順序的步驟：

1. 每一個路徑元件`X`為其`is_symlink(X)`是 **，則為 true**取代`read_symlink(X)`。

1. 每一個路徑元件`.`（點是目前的目錄，由上一個路徑元件所建立） 已移除。

1. 每一對路徑元件`X` / `..` （點點是由上一個路徑元件所建立的父目錄） 中移除。

函式會傳回`pabs`。

## <a name="copy"></a>  copy

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

函式都可能複製或連結在一或多個檔案*從*要*來*控制*opts*，這會被視為`copy_options::none`沒有的多載*opts*參數。 *opts*應該包含最多是其中之一：

- `skip_existing`、 `overwrite_existing`或 `update_existing`

- `copy_symlinks` 或 `skip_symlinks`

- `directories_only`、 `create_symlinks`或 `create_hard_links`

函式會先判斷的 file_status 值`f`針對*從*並`t`如*來*:

- 如果`opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`，藉由呼叫 `symlink_status`

- 否則，藉由呼叫 `status`

- 再則報告錯誤。

如果`!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`，他們接著會報告錯誤 （並不執行任何其他）。

否則，如果`is_symlink(f)`然後：

- 如果`options & copy_options::skip_symlinks`不執行任何動作。

- 否則，如果`!exists(t)&& options & copy_options::copy_symlinks`然後`copy_symlink(from, to, opts)`。

- 再則報告錯誤。

否則，如果`is_regular_file(f)`然後：

- 如果`opts & copy_options::directories_only`不執行任何動作。

- 否則，如果`opts & copy_options::create_symlinks`然後`create_symlink(to, from)`。

- 否則，如果`opts & copy_options::create_hard_links`然後`create_hard_link(to, from)`。

- 否則，如果`is_directory(f)`再`copy_file(from, to`  /  `from.filename(), opts)`。

- 否則為 `copy_file(from, to, opts)`。

否則，如果`is_directory(f) && (opts & copy_options::recursive || !opts)`然後：

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

## <a name="copy_file"></a>  copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

函式都可能複製的檔案*從*要*來*控制*opts*，這會被視為`copy_options::none`沒有多載*opts*參數。 *opts*應該包含最多是其中一個`skip_existing`， `overwrite_existing`，或`update_existing`。

如果`exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`則報告檔案已存在的錯誤。

否則，如果`!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`再嘗試複製的內容和檔案的屬性*從*souboru*到*。 如果複製嘗試失敗，則報告錯誤。

函式會傳回**真**如果複製嘗試和成功，否則為**false**。

## <a name="copy_symlink"></a>  copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

如果`is_directory(from)`函式呼叫`create_directory_symlink(from, to)`。 否則，它會呼叫`create_symlink(from, to)`。

## <a name="create_directories"></a>  create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

若是 a\/b\/c 這類的路徑名稱，函式會視需要建立目錄 a 和 a\/b，以便有必要時可以建立目錄 a\/b\/c。 它會傳回**真**確實建立目錄時，才*pval*。

## <a name="create_directory"></a>  create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

此函式會建立目錄*pval*視。 它只會傳回 true 確實建立目錄*pval*，在此情況下它會將複製的權限從現有的檔案*attr*，或使用`perms::all`沒有多載*attr*參數。

## <a name="create_directory_symlink"></a>  create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

此函式會建立連結當做至目錄的符號連結*至*。

## <a name="create_hard_link"></a>  create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

函式會建立為目錄或檔案的硬式連結的連結*至*。

## <a name="create_symlink"></a>  create_symlink

```cpp
void create_symlink(const path& to,  const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

函式會建立*連結*當做檔案的符號連結*至*。

## <a name="current_path"></a>  current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

不含參數的函式*pval*傳回目前目錄的路徑名稱。 其餘的函式會將目前的目錄設定為*pval*。

## <a name="end"></a>  end

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

第一個函式會傳回`directory_iterator()`，第二個函式傳回 `recursive_directory_iterator()`

## <a name="equivalent"></a>  equivalent

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

函式會傳回 **，則為 true**只有當*左*並*右*指定相同的檔案系統實體。

## <a name="exists"></a>  exists

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `status_known && stat.type() != file_not_found`。 第二個和第三個函式會傳回`exists(status(pval))`。

## <a name="file_size"></a>  file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

函式會傳回大小，以位元組為單位的所指定的檔案*pval*，如果`exists(pval) && is_regular_file(pval)`，並且可以判斷檔案的大小。 否則它們會報告錯誤並傳回`uintmax_t(-1)`。

## <a name="hard_link_count"></a>  hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

函數會傳回的永久連結數目*pval*，或\-1 發生錯誤。

## <a name="hash_value"></a>  hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

函式會傳回雜湊值`pval.native()`。

## <a name="is_block_file"></a>  is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::block`。 其餘函式會傳回`is_block_file(status(pval))`。

## <a name="is_character_file"></a>  is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::character`。 其餘函式會傳回`is_character_file(status(pval))`。

## <a name="is_directory"></a>  is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::directory`。 其餘函式會傳回`is_directory_file(status(pval))`。

## <a name="is_empty"></a>  is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

如果`is_directory(pval)`則函式會傳回`directory_iterator(pval) == directory_iterator()`; 否則會傳回`file_size(pval) == 0`。

## <a name="is_fifo"></a>  is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::fifo`。 其餘函式會傳回`is_fifo(status(pval))`。

## <a name="is_other"></a>  is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::other`。 其餘函式會傳回`is_other(status(pval))`。

## <a name="is_regular_file"></a>  is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::regular`。 其餘函式會傳回`is_regular_file(status(pval))`。

## <a name="is_socket"></a>  is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::socket`。 其餘函式會傳回`is_socket(status(pval))`。

## <a name="is_symlink"></a>  is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::symlink`。 其餘函式會傳回`is_symlink(status(pval))`。

## <a name="last_write_time"></a>  last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

前兩個函式會傳回一次資料修改的時間*pval*，或`file_time_type(-1)`發生錯誤。 最後兩個函式會將一次資料修改的時間*pval*要*new_time*。

## <a name="permissions"></a>  permissions

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

函式會將指定的路徑名稱的權限*pval*要`mask & perms::mask`控制`perms & (perms::add_perms | perms::remove_perms)`。 *遮罩*應該包含最多是其中一個`perms::add_perms`和`perms::remove_perms`。

如果`mask & perms::add_perms`函式設定權限`status(pval).permissions() | mask & perms::mask`。 否則，如果`mask & perms::remove_perms`函式設定權限`status(pval).permissions() & ~(mask & perms::mask)`。 否則，函式會將權限`mask & perms::mask`。

## <a name="read_symlink"></a>  read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

函式會報告錯誤並傳回`path()`如果`!is_symlink(pval)`。 否則，函數會傳回包含符號連結的 `path` 類型物件。

## <a name="remove"></a>  remove

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

函式會傳回**真**只有當`exists(symlink_status(pval))`，而且已成功移除檔案。 符號連結移除了自己本身，不是它指定的檔案。

## <a name="remove_all"></a>  remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

如果*pval*是目錄，函式以遞迴方式移除所有目錄項目，則項目本身。 否則，函式呼叫`remove`。 它們會傳回成功移除的所有元素計數。

## <a name="rename"></a>  rename

```cpp
void rename(const path& from,  const path& to);
void rename(const path& from,  const path& to, error_code& ec) noexcept;
```

函式重新命名*從*要*至*。 符號連結重新命名了自己本身，不是它指定的檔案。

## <a name="resize_file"></a>  resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

函式變更檔案的大小， `file_size(pval) == size`

## <a name="space"></a>  space

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

函式會傳回指定的磁碟區的相關資訊*pval*，在結構中的型別`space_info`。 此結構包含`uintmax_t(-1)`無法判斷任何值。

## <a name="status"></a>  status

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

函式會傳回路徑名稱狀態、 檔案類型和權限，與相關聯*pval*。 系統並不會測試符號連結本身，但會測試其指定的檔案。

## <a name="status_known"></a>  status_known

```cpp
bool status_known(file_status stat) noexcept;
```

在函式傳回 `stat.type() != file_type::none`

## <a name="swap"></a>  swap

```cpp
void swap(path& left, path& right) noexcept;
```

函式會交換的內容*左*並*右*。

## <a name="symlink_status"></a>  symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

函式會傳回路徑名稱符號連結狀態、 檔案類型和權限，與相關聯*pval*。 函式的行為相同`status(pval)`不同之處在於符號連結是測試本身，不其指定的檔案。

## <a name="system_complete"></a>  system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

函式會傳回有必要納入考量的絕對路徑名稱，與其根名稱相關聯之目前的目錄。 \(至於 Posix，函式會傳回`absolute(pval)`。\)

## <a name="temp_directory_path"></a>  temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

函式會傳回適合包含暫存檔的目錄路徑名稱。

## <a name="u8path"></a>  u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

第一個函式的行為相同`path(source)`和第二個函式的行為相同`path(first, last)`不同之處在於每個案例中指定的來源會被視為一串字元編碼為 utf-8，不論檔案系統的項目。
