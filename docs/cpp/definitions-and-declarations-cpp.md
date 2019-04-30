---
title: 定義和宣告 (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: 987e27bdf35eba7d9380fc546c15b93b3179333b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392241"
---
# <a name="definitions-and-declarations-c"></a>定義和宣告 (C++)

**Microsoft 專屬**

DLL 介面會參考已知由系統; 中匯出的某些程式的所有項 （函式和資料）也就是說，所有的項目宣告為**dllimport**或是**dllexport**。 DLL 介面中的所有宣告都必須都指定**dllimport**或是**dllexport**屬性。 不過，定義必須只指定**dllexport**屬性。 例如，下列函式定義會產生編譯器錯誤：

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

善用**dllexport**隱含了定義，而**dllimport**隱含了宣告。 您必須使用**extern**關鍵字搭配**dllexport**強制宣告; 定義隱含的否則為。 因此，下列範例是正確的：

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

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[dllexport、dllimport](../cpp/dllexport-dllimport.md)