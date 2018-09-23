---
title: 定義和宣告 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae97ecc055ed7e6a448f2f820e762cafb2c5798
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028671"
---
# <a name="definitions-and-declarations-c"></a>定義和宣告 (C)

**Microsoft 專屬**

DLL 介面會參考已知由系統中某些程式匯出的所有項目 (函式和資料)，也就是宣告為 **dllimport`dllexport` 或**  的所有項目。 DLL 介面中的所有宣告都必須指定 **dllimport`dllexport` 或**  屬性。 不過，此定義只能指定 `dllexport` 屬性。 例如，下列函式定義會產生編譯器錯誤：

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

使用 `dllexport` 隱含了定義，而 **dllimport** 則隱含了宣告。 您必須使用 `extern` 關鍵字搭配 `dllexport` 以強制進行宣告，否則其中會隱含宣告。

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllImport int k;   /* These are correct and imply */
Dllimport int j;          /* a declaration. */
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[DLL 匯入及匯出函式](../c-language/dll-import-and-export-functions.md)