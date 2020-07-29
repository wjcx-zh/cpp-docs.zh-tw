---
title: 定義和宣告 (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: c35c0adaa1b81e5bf9bfd9e779037bc6068b3174
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221701"
---
# <a name="definitions-and-declarations-c"></a>定義和宣告 (C++)

**Microsoft 特定的**

DLL 介面會參考系統中某些程式所能匯出的所有專案（函式和資料）;也就是宣告為或的所有專案 **`dllimport`** **`dllexport`** 。 包含在 DLL 介面中的所有宣告都必須指定 **`dllimport`** 或 **`dllexport`** 屬性。 不過，定義必須僅指定 **`dllexport`** 屬性。 例如，下列函式定義會產生編譯器錯誤：

```
__declspec( dllimport ) int func() {   // Error; dllimport
                                       // prohibited on definition.
   return 1;
}
```

此程式碼也會產生錯誤：

```
__declspec( dllimport ) int i = 10;  // Error; this is a definition.
```

不過，這個語法是正確的：

```
__declspec( dllexport ) int i = 10;  // Okay--export definition
```

使用 **`dllexport`** 表示定義，而則表示宣告 **`dllimport`** 。 您必須搭配使用 **`extern`** 關鍵字 **`dllexport`** 來強制執行宣告，否則會隱含定義。 因此，下列範例是正確的：

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllExport int k; // These are both correct and imply a
DllImport int j;        // declaration.
```

下列範例釐清前述範例：

```
static __declspec( dllimport ) int l; // Error; not declared extern.

void func() {
    static __declspec( dllimport ) int s;  // Error; not declared
                                           // extern.
    __declspec( dllimport ) int m;         // Okay; this is a
                                           // declaration.
    __declspec( dllexport ) int n;         // Error; implies external
                                           // definition in local scope.
    extern __declspec( dllimport ) int i;  // Okay; this is a
                                           // declaration.
    extern __declspec( dllexport ) int k;  // Okay; extern implies
                                           // declaration.
    __declspec( dllexport ) int x = 5;     // Error; implies external
                                           // definition in local scope.
}
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[dllexport、dllimport](../cpp/dllexport-dllimport.md)
