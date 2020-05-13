---
title: 使用 .DEF 檔匯入
ms.date: 11/04/2016
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
ms.openlocfilehash: 13a6a375d6200f73dd9845d057d1954c2b65485c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273413"
---
# <a name="importing-using-def-files"></a>使用 .DEF 檔匯入

如果您選擇使用 **__declspec （dllimport）** 搭配 .def 檔案，您應該變更 .def 檔案以使用資料來取代常數，以降低不正確編碼的機率會造成問題的可能性：

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

下表顯示原因。

|關鍵字|在匯入程式庫中發出|多餘|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

使用 **__declspec （dllimport）** 和常數會在建立`imp`來允許明確連結的 .LIB DLL 匯入程式庫中，列出版本和未裝飾名稱稱。 使用 **__declspec （dllimport）** 和資料只會列出`imp`名稱的版本。

如果您使用常數，可以使用下列其中一個程式碼結構來存取`ulDataInDll`：

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\-或-

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

不過，如果您使用 .def 檔案中的資料，則只有使用下列定義編譯的程式碼才能存取變數`ulDataInDll`：

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

使用常數會更有風險，因為如果您忘了使用額外的間接取值層級，您可能會存取匯入位址資料表的指標，而不是變數本身。 這種類型的問題通常會因為編譯器和連結器的匯入位址資料表是唯讀的，而視為存取違規。

如果目前的 MSVC 連結器在 .def 檔案中看到常數，就會發出警告，以考慮這種情況。 唯一使用常數的真正原因是，如果您無法重新編譯某個檔案，其中標頭檔不會列出原型上的 **__declspec （dllimport）** 。

## <a name="see-also"></a>請參閱

[匯入至應用程式](importing-into-an-application.md)
