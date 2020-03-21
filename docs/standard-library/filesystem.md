---
title: '&lt;filesystem&gt;'
description: 描述標準C++程式庫的 filesystem 標頭中的類別、函式和類型。
ms.date: 01/22/2020
f1_keywords:
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
no-loc:
- filesystem
- experimental
- char
- wchar_t
- char16_t
- char32_t
ms.openlocfilehash: 86be11da1e2cef2fe0ca12691aeb0ce3dbe94202
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076502"
---
# &lt;filesystem&gt;

包含標頭 &lt;filesystem>，以存取可操作和抓取路徑、檔案和目錄相關資訊的類別和函式。

## <a name="syntax"></a>語法

```cpp
#include <filesystem> // C++17 standard header file name
#include <experimental/filesystem> // Header file for pre-standard implementation
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> 在 Visual Studio 2017 的版本中，\<filesystem> 標頭尚未是C++標準。 C++在 Visual Studio 2017 RTW 中，會採用[ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100)中所找到的最終草稿標準。 Visual Studio 2017 15.7 版和更新版本支援新的 c + + 17 \<filesystem> standard。
> 這是全新的執行，與先前的 `std::experimental` 版本不相容。 它是透過連結支援、bug 修正，以及標準所需行為的變更所進行的。 目前，包括 \<filesystem> 會提供新的 `std::filesystem` 和先前的 `std::experimental::filesystem`。 包括 \<experimental/filesystem> 只會提供舊的 experimental 執行。 系統會在下一次 ABI 中斷的程式庫中移除 experimental 的執行。

此標頭支援下列兩個廣泛類別的主機作業系統之一的檔案系統： Microsoft Windows 和 POSIX。

雖然大部分功能對這兩個作業系統而言是共通的，不過本文還是指出其中的差異。 例如：

- Windows 支援多個根名稱，例如 `c:` 或 `\\network_name`。 檔案系統是由樹狀結構樹系所組成，每個都有自己的根目錄，例如 `c:\` 或 `\\network_name\`，而每個都有其本身的目前的目錄，以完成相對路徑名稱（不是絕對路徑名稱的一個）。

- POSIX 支援單一樹狀結構，其中沒有根名稱、單一根目錄 `/`和單一目前的目錄。

另一項重大差異是路徑名稱的原生表示法：

- Windows 使用以 null 終止的 **wchar_t** 序列，並編碼為 utf-16 （每個字元有一或多個元素）。

- POSIX 會使用以 null 終止的 **char** 序列，並編碼為 utf-8 （每個字元有一或多個元素）。

- 類別的物件 `path` 以原生格式儲存路徑名稱，但支援在此儲存的表單和數個外部表單之間輕鬆轉換：

  - 以 null 終止的 **char** 序列，以作業系統的偏好進行編碼。

  - 以 null 終止的 **char** 序列，已編碼為 utf-8。

  - 以 null 終止的 **wchar_t** 序列，以作業系統的偏好進行編碼。

  - 以 null 終止的 **char16_t** 序列，並編碼為 utf-16。

  - 以 null 終止的 **char32_t** 序列，編碼為 UTF-32。

  請視需要考慮使用一或多個 `codecvt` Facet，在這些表示法之間進行轉換。 如果未指定特定的地區設定物件，則會從全域地區設定取得這些 facet。

另一項差異是每個作業系統讓您用來指定檔案或目錄存取權限的詳細資料：

- Windows 會記錄檔案是否為唯讀或可寫入，也就是沒有目錄意義的屬性。

- POSIX 會記錄檔案是否可以讀取、寫入或執行（掃描目錄）。 而且，無論擁有者、擁有者群組或每個人都允許每項作業，再加上一些其他許可權。

這兩個系統在根目錄名稱之後有通用的路徑名稱結構。 針對 pathname `c:/abc/xyz/def.ext`：

- 根名稱為 `c:`。

- 根目錄是 `/`。

- 根路徑為 `c:/`。

- 相對路徑為 `abc/xyz/def.ext`。

- 父路徑為 `c:/abc/xyz`。

- 檔案名稱為 `def.ext`。

- 此詞幹 `def`。

- 延伸模組為 `.ext`。

次要差異是路徑名稱中目錄序列之間的慣用分隔符號。 這兩個作業系統都可讓您撰寫正斜線 `/`，但在某些內容中，Windows 偏好使用反斜線 `\`。 此實作為在 `path`的資料成員 `preferred_separator` 中儲存其慣用分隔符號。

最後，`path` 物件有一項重要的功能：您可以使用它們，只要在標頭中定義的類別中必須有 filename 引數[\<a m >](fstream.md)。

如需詳細資訊和程式碼範例，請參閱[檔C++系統導覽（）](../standard-library/file-system-navigation.md)。

## <a name="members"></a>成員

### <a name="classes"></a>類別

|||
|-|-|
|[directory_entry 類別](../standard-library/directory-entry-class.md)|描述 `directory_iterator` 或 `recursive_directory_iterator` 傳回的物件，並包含 `path`。|
|[directory_iterator 類別](../standard-library/directory-iterator-class.md)|描述可循序遍訪檔案系統目錄中的檔案名稱的輸入迭代器。|
|[filesystem_error 類別](../standard-library/filesystem-error-class.md)|擲回例外狀況的基底類別，以報告低階系統溢位。|
|[path 類別](../standard-library/path-class.md)|定義一個類別，以儲存適合做為檔案名稱之樣板類型 `String` 的物件。|
|[recursive_directory_iterator 類別](../standard-library/recursive-directory-iterator-class.md)|描述可循序遍訪檔案系統目錄中的檔案名稱的輸入迭代器。 迭代器也可以下降到子目錄。|
|[file_status 類別](../standard-library/file-status-class.md)|包裝 `file_type`。|

### <a name="structs"></a>結構

|||
|-|-|
|[space_info 結構](../standard-library/space-info-structure.md)|保留磁碟區的相關資訊。|

## <a name="functions"></a>Functions

[\<filesystem> 函數](../standard-library/filesystem-functions.md)

## <a name="operators"></a>操作員

[\<filesystem> 運算子](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>列舉

|||
|-|-|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|列舉搭配使用 [copy_file](../standard-library/filesystem-functions.md#copy_file) ，並在已存在目的地檔案時決定行為。|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|指定目錄迭代器之選項的列舉。|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|檔案類型的列舉。|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)| 列舉 `permissions` 函數的選項。 |
|[perms](../standard-library/filesystem-enumerations.md#perms)|用來傳達權限和權限選項的位元遮罩類型|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
