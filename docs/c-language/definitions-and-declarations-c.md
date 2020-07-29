---
title: 定義和宣告 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
ms.openlocfilehash: 0e39832f942eb1473be913112fde1d37ddf05674
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226362"
---
# <a name="definitions-and-declarations-c"></a>定義和宣告 (C)

**Microsoft 特定的**

DLL 介面會參考系統中某些程式所能匯出的所有專案（函式和資料）;也就是宣告為或的所有專案 **`dllimport`** `dllexport` 。 包含在 DLL 介面中的所有宣告都必須指定 **`dllimport`** 或 `dllexport` 屬性。 不過，此定義只能指定 `dllexport` 屬性。 例如，下列函式定義會產生編譯器錯誤：

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int func()    /* Error; dllimport prohibited in */
                        /* definition. */
{
   return 1;
}
```

此程式碼也會產生錯誤：

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int i = 10;      /* Error; this is a definition. */
```

不過，這個語法是正確的：

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport int i = 10;      /* Okay: this is an export definition. */
```

使用 `dllexport` 表示定義，而則表示宣告 **`dllimport`** 。 您必須搭配使用 **`extern`** 關鍵字 `dllexport` 來強制執行宣告，否則會隱含定義。

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllImport int k;   /* These are correct and imply */
Dllimport int j;          /* a declaration. */
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[DLL 匯入和匯出函式](../c-language/dll-import-and-export-functions.md)
