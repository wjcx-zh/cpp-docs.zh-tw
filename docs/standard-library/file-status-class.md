---
title: file_status 類別
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::file_status
- filesystem/std::experimental::filesystem::file_status::operator=
- filesystem/std::experimental::filesystem::file_status::type
- filesystem/std::experimental::filesystem::file_status::permissions
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
helpviewer_keywords:
- std::experimental::filesystem::file_status
- std::experimental::filesystem::file_status::operator=
- std::experimental::filesystem::file_status::type
- std::experimental::filesystem::file_status::permissions
ms.openlocfilehash: 60ced1f60c811f585928f47c6cfd5e695d0c4085
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457744"
---
# <a name="filestatus-class"></a>file_status 類別

包裝 [file_type](../standard-library/filesystem-enumerations.md#file_type) 和檔案的 [perms](../standard-library/filesystem-enumerations.md#perms)。

## <a name="syntax"></a>語法

```cpp
class file_status;
```

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[file_status](#file_status)|為[file_type](../standard-library/filesystem-enumerations.md#file_type)和檔案[perms](../standard-library/filesystem-enumerations.md#perms)結構建立包裝函式。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[type](#type)|取得或設定 `file_type`。|
|[permissions](#permissions)|取得或設定檔案權限。|

### <a name="operators"></a>運算子

|運算子|說明|
|-|-|
|[operator=](#op_as)|預設成員指派運算子會如預期般運作。|

## <a name="requirements"></a>需求

**標頭:** \<filesystem >

**命名空間:** std:: 實驗性:: filesystem、std:: 實驗性:: filesystem

## <a name="file_status"></a>file_status::file_status

為[file_type](../standard-library/filesystem-enumerations.md#file_type)和檔案[perms](../standard-library/filesystem-enumerations.md#perms)結構建立包裝函式。

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>參數

*ftype*\
指定`file_type`時, 預設`file_type::none`為。

*遮罩*\
指定的檔案`perms::unknown` ,`perms`預設值為。

*file_status*\
儲存的物件。

## <a name="op_as"></a>file_status:: operator =

預設成員指派運算子會如預期般運作。

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>參數

*file_status*\
要[](../standard-library/file-status-class.md)複製到`file_status`中的 file_status。

## <a name="type"></a>型

取得或設定 `file_type`。

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>參數

*ftype*\
已指定 `file_type`。

## <a name="permissions"></a>無權

取得或設定檔案權限。

使用 setter 來建立`readonly`檔案或`readonly`移除屬性。

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>參數

*遮罩*\
已指定 `perms`。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[path 類別](../standard-library/path-class.md)\
[\<filesystem>](../standard-library/filesystem.md)
