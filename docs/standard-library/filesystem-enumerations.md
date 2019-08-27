---
title: '&lt;filesystem&gt; 列舉'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::filesystem::copy_options
- filesystem/std::experimental::filesystem::copy_options
- filesystem/std::filesystem::directory_options
- filesystem/std::experimental::filesystem::directory_options
- filesystem/std::filesystem::file_type
- filesystem/std::experimental::filesystem::file_type
- filesystem/std::filesystem::perms
- filesystem/std::experimental::filesystem::perms
ms.assetid: 0096c046-d101-464c-8259-b878a48280b0
ms.openlocfilehash: dfbcf65462f0bb7bc6ca44f43507efa7b753e7bc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457717"
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;filesystem&gt; 列舉

本主題說明檔案系統標頭中的列舉。

## <a name="requirements"></a>需求

**標頭：** \<experimental/filesystem>

**命名空間：** std::experimental::filesystem

## <a name="copy_options"></a>  copy_options

此位元遮罩值的列舉可搭配 [copy](filesystem-functions.md#copy) 和 [copy_file](filesystem-functions.md#copy_file) 函式來指定行為。

### <a name="syntax"></a>語法

```cpp
enum class copy_options {
   none = 0,
   skip_existing = 1,
   overwrite_existing = 2,
   update_existing = 4,
   recursive = 8,
   copy_symlinks = 16,
   skip_symlinks = 32,
   directories_only = 64,
   create_symlinks = 128,
   create_hard_links = 256
};
```

### <a name="values"></a>值

|`Name`|描述|
|------------|-----------------|
|`none`|執行作業的預設行為。|
|`skip_existing`|若檔案已經存在，請不要複製，也不要回報錯誤。|
|`overwrite_existing`|如果已經存在，請覆寫檔案。|
|`update_existing`|如果檔案已經存在但比取代版更舊，請覆寫檔案。|
|`recursive`|以遞迴方式複製子目錄和其內容。|
|`copy_symlinks`|請直接複製符號連結，而不要複製其所指向的檔案。|
|`skip_symlinks`|略過符號連結。|
|`directories_only`|僅逐一查看目錄，而略過檔案。|
|`create_symlinks`|建立符號連結，而不要複製檔案。 除非目的地是目前的目錄，否則就必須將絕對路徑作為來源路徑。|
|`create_hard_links`|建立永久連結，而不要複製檔案。|

## <a name="directory_options"></a> directory_options

指定是否要遵循目錄的符號連結，或忽略它們。

### <a name="syntax"></a>語法

```cpp
enum class directory_options {
   none = 0,
   follow_directory_symlink
};
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`none`|預設行為︰忽略目錄的符號連結。 權限遭拒是一種錯誤。|
|`follow_directory_symlink`|將目錄的符號連結視為實際的目錄。|

## <a name="file_type"></a>  file_type

檔案類型的列舉。 支援的值為 regular、directory、not_found 和 unknown。

### <a name="syntax"></a>語法

```cpp
enum class file_type {
    not_found = -1,
    none,
    regular,
    directory,
    symlink,
    block,
    character,
    fifo,
    socket,
    unknown
};
```

### <a name="values"></a>值

|名稱|值|說明|
|----------|-----------|-----------------|
|`not_found`|-1|代表不存在的檔案。|
|`none`|0|代表不具有類型屬性的檔案。 (不支援。)|
|`regular`|1|代表傳統的磁碟檔案。|
|`directory`|2|代表目錄。|
|`symlink`|3|代表符號連結。 (不支援。)|
|`block`|4|代表 UNIX 系統上的區塊專用檔案。 (不支援。)|
|`character`|5|代表 UNIX 系統上的字元專用檔案。 (不支援。)|
|`fifo`|6|代表 UNIX 系統上的 FIFO 檔案。 (不支援。)|
|`socket`|7|代表 UNIX 系統上的通訊端。 (不支援。)|
|`unknown`|8|代表無法判斷狀態的檔案。|

## <a name="perm_options"></a>perm_options

包含值`replace` `add` 、、和`nofollow`。 `remove`

```cpp
enum class perm_options;
```

## <a name="perms"></a>  perms

檔案權限的旗標。 支援的值基本上為 "readonly" 和 all。 對於唯讀檔案，未設定任何 *_write 位元。 否則會設定 `all` 位元 (0x0777)。

### <a name="syntax"></a>語法

```cpp
enum class perms {// names for permissions
   none = 0,
   owner_read = 0400,  // S_IRUSR
   owner_write = 0200, // S_IWUSR
   owner_exec = 0100,  // S_IXUSR
   owner_all = 0700,   // S_IRWXU
   group_read = 040,   // S_IRGRP
   group_write = 020,  // S_IWGRP
   group_exec = 010,   // S_IXGRP
   group_all = 070,    // S_IRWXG
   others_read = 04,   // S_IROTH
   others_write = 02,  // S_IWOTH
   others_exec = 01,   // S_IXOTH
   others_all = 07,    // S_IRWXO
   all = 0777,
   set_uid = 04000,    // S_ISUID
   set_gid = 02000,    // S_ISGID
   sticky_bit = 01000, // S_ISVTX
   mask = 07777,
   unknown = 0xFFFF,
   add_perms = 0x10000,
   remove_perms = 0x20000,
   resolve_symlinks = 0x40000
};
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)
