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
ms.openlocfilehash: 1ab57a6fc13a03d02963f3d7ecc80f63decb9487
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875817"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt; 函式

[\<filesystem >](../standard-library/filesystem.md)標頭中的這些免費功能，會在路徑、檔案、符號連結、目錄和磁片區上修改和查詢作業。 如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。

## <a name="absolute"></a>求

```cpp
path absolute(const path& pval, const path& base = current_path());
```

函式會傳回相對於路徑名稱 `base`之對應至*pval*的絕對路徑名稱：

1. 如果 `pval.has_root_name() && pval.has_root_directory()` 函數會傳回*pval*。

1. 如果 `pval.has_root_name() && !pval.has_root_directory()` 函式會傳回 `pval.root_name()` / `absolute(base).root_directory()` / `absolute(base).relative_path()` / `pval.relative_path()`。

1. 如果 `!pval.has_root_name() && pval.has_root_directory()` 函式會傳回 `absolute(base).root_name()` / *pval*。

1. 如果 `!pval.has_root_name() && !pval.has_root_directory()` 函式會傳回 `absolute(base)` / *pval*。

## <a name="begin"></a>起點

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

這兩個函數都會傳回*iter*。

## <a name="canonical"></a>標準

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

函式全都形成絕對路徑名稱 `pabs = absolute(pval, base)` （或 `pabs = absolute(pval)` 沒有基底參數的多載），然後依照下列步驟順序將它縮減為標準格式：

1. `is_symlink(X)` 為**true**的每個路徑元件 `X` 都會由 `read_symlink(X)`所取代。

1. 已移除每個路徑元件 `.` （點是由先前路徑元件所建立的目前目錄）。

1. `X`/`..` 的每一對路徑元件（點點點是先前路徑元件所建立的上層目錄）都會移除。

函數接著會傳回 `pabs`。

## <a name="copy"></a>複製

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

函式可能會將中的一個或多個檔案*從*複製或連結至，*以*控制 [選擇 *]，這*會以*不含選擇參數的*多載 `copy_options::none` 來取得。 選擇最*多隻能包含*其中一個：

- `skip_existing`、`overwrite_existing` 或 `update_existing`

- `copy_symlinks` 或 `skip_symlinks`

- `directories_only`、`create_symlinks` 或 `create_hard_links`

函式會先判斷 *`f` 的 file_status*值 *，並將 `t` 為：*

- 如果 `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`，則呼叫 `symlink_status`

- 否則，藉由呼叫 `status`

- 再則報告錯誤。

如果 `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`，則會報告錯誤（並不執行任何動作）。

否則，如果 `is_symlink(f)`，則：

- 如果 `options & copy_options::skip_symlinks`，則不執行任何動作。

- 否則，如果 `!exists(t)&& options & copy_options::copy_symlinks`，則 `copy_symlink(from, to, opts)`。

- 否則，報告錯誤。

否則，如果 `is_regular_file(f)`，則：

- 如果 `opts & copy_options::directories_only`，則不執行任何動作。

- 否則，如果 `opts & copy_options::create_symlinks`，則 `create_symlink(to, from)`。

- 否則，如果 `opts & copy_options::create_hard_links`，則 `create_hard_link(to, from)`。

- 否則，如果 `is_directory(f)`，則 `copy_file(from, to` / `from.filename(), opts)`。

- 否則為 `copy_file(from, to, opts)`。

否則，如果 `is_directory(f) && (opts & copy_options::recursive || !opts)`，則：

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

## <a name="copy_file"></a>copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

函式可能會將中的檔案*從*複製到，*以*控制*選擇，這*會以*不含選擇參數的*多載 `copy_options::none` 的方式來取得。 選擇項最*多隻能包含*一個 `skip_existing`、`overwrite_existing`或 `update_existing`。

如果 `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`，則會回報為檔案已存在的錯誤。

否則，如果 `!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`，則會嘗試將檔案的內容和屬性*從* *複製到檔案。* 如果複製嘗試失敗，則報告錯誤。

如果嘗試複製並成功，函數會傳回**true** ，否則傳回**false**。

## <a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

如果 `is_directory(from)`，則函數會呼叫 `create_directory_symlink(from, to)`。 否則，它會呼叫 `create_symlink(from, to)`。

## <a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

對於\/b\/c 之類的路徑名稱，此函式會視需要建立目錄 a 和\/b，使其可以視需要建立\/b\/c 目錄。 只有在實際建立目錄*pval*時，才會傳回**true** 。

## <a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

函式會視需要建立目錄*pval* 。 只有在實際建立目錄*pval*時，才會傳回 true，在此情況下，它會從現有的檔案*attr*複製許可權，或使用沒有*attr*參數的多載 `perms::all`。

## <a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

函式會將連結*建立為的目錄的*符號。

## <a name="create_hard_link"></a>create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

函式會將連結建立為目錄或檔案的硬式*連結。*

## <a name="create_symlink"></a>create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

函式會建立*連結*，做為將檔案加入*至*的符號。

## <a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

沒有參數*pval*的函式會傳回目前目錄的路徑名稱。 其餘的函式會將目前的目錄設定為*pval*。

## <a name="end"></a>  end

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

第一個函式會傳回 `directory_iterator()`，而第二個函數會傳回 `recursive_directory_iterator()`

## <a name="equivalent"></a>價額

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

只有當*left*和*right*選擇同一個 filesystem 實體時，函數才會傳回**true** 。

## <a name="exists"></a>  exists

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `status_known && stat.type() != file_not_found`。 第二個和第三個函式會傳回 `exists(status(pval))`。

## <a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

函式會傳回*pval*所選擇之檔案的大小（以位元組為單位），如果可以判斷 `exists(pval) && is_regular_file(pval)` 和檔案大小。 否則，它們會報告錯誤並傳回 `uintmax_t(-1)`。

## <a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

函式會傳回*pval*的永久連結數目，如果發生錯誤，則為 \-1。

## <a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

函數會傳回 `pval.native()`的雜湊值。

## <a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::block`。 其餘的函數會傳回 `is_block_file(status(pval))`。

## <a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::character`。 其餘的函數會傳回 `is_character_file(status(pval))`。

## <a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::directory`。 其餘的函數會傳回 `is_directory_file(status(pval))`。

## <a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

如果 `is_directory(pval)`，則函數會傳回 `directory_iterator(pval) == directory_iterator()`;否則，它會傳回 `file_size(pval) == 0`。

## <a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::fifo`。 其餘的函數會傳回 `is_fifo(status(pval))`。

## <a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::other`。 其餘的函數會傳回 `is_other(status(pval))`。

## <a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::regular`。 其餘的函數會傳回 `is_regular_file(status(pval))`。

## <a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::socket`。 其餘的函數會傳回 `is_socket(status(pval))`。

## <a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

第一個函式會傳回 `stat.type() == file_type::symlink`。 其餘的函數會傳回 `is_symlink(status(pval))`。

## <a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

前兩個函式會傳回*pval*上次修改資料的時間，如果發生錯誤，則傳回 `file_time_type(-1)`。 最後兩個函式會將*pval*的上次資料修改時間設定為*new_time*。

## <a name="permissions"></a>無權

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

函式會將*pval*所選擇之路徑名稱的許可權設定為 `perms & (perms::add_perms | perms::remove_perms)`控制之下的 `mask & perms::mask`。 *遮罩*最多隻能包含其中一個 `perms::add_perms` 和 `perms::remove_perms`。

如果 `mask & perms::add_perms`，函式會將許可權設定為 `status(pval).permissions() | mask & perms::mask`。 否則，如果 `mask & perms::remove_perms`，函式會將許可權設定為 `status(pval).permissions() & ~(mask & perms::mask)`。 否則，函數會將許可權設定為 `mask & perms::mask`。

## <a name="proximate"></a>鄰近

```cpp
path proximate(const path& p, error_code& ec);
path proximate(const path& p, const path& base = current_path());
path proximate(const path& p, const path& base, error_code& ec);
```

## <a name="read_symlink"></a>read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

函式會報告錯誤，並在 `!is_symlink(pval)`時傳回 `path()`。 否則，函數會傳回包含符號連結的 `path` 類型物件。

## <a name="relative"></a>相比

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a>取消

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

只有在 `exists(symlink_status(pval))` 且成功移除檔案時，函數才會傳回**true** 。 已移除符號，而不是它所選擇的檔案。

## <a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

如果*pval*是目錄，函式會以遞迴方式移除所有目錄專案，然後是專案本身。 否則，函數會呼叫 `remove`。 它們會傳回成功移除的所有元素計數。

## <a name="rename"></a>rename

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

函式會將*從*重新命名*為。* 符號會重新命名，而不是它所選擇的檔案。

## <a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

函式會改變檔案的大小，使其 `file_size(pval) == size`

## <a name="space"></a>space

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

函式會在 `space_info`類型的結構中，傳回*pval*所選磁片區的相關資訊。 結構包含無法判斷之任何值的 `uintmax_t(-1)`。

## <a name="status"></a>狀態

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

函式會傳回與*pval*相關聯的路徑名稱狀態、檔案類型和許可權。 「符號」本身並不會經過測試，而是它所選擇的檔案。

## <a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

函式會傳回 `stat.type() != file_type::none`

## <a name="swap"></a>調換

```cpp
void swap(path& left, path& right) noexcept;
```

函式會交換*left*和*right*的內容。

## <a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

函式會傳回與*pval*相關聯的路徑名稱連結狀態、檔案類型和許可權。 函式的行為與 `status(pval)` 相同，不同之處在于會自行測試連結符號，而不是它所選擇的檔案。

## <a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

函式會傳回有必要納入考量的絕對路徑名稱，與其根名稱相關聯之目前的目錄。 \(POSIX，函式會傳回 `absolute(pval)`。\)

## <a name="temp_directory_path"></a>temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

函式會傳回適合包含暫存檔的目錄路徑名稱。

## <a name="u8path"></a>u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

第一個函式的行為與 `path(source)` 相同，而第二個函式的行為與 `path(first, last)` 相同，不同之處在于每個案例中所選的來源會視為編碼為 UTF-8 的 char 元素序列（無論檔案系統為何）。

## <a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
