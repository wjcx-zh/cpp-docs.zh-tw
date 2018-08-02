---
title: 定義和宣告 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d192234a2b3cd3d72bef15e11678ebc41ccede0
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462884"
---
# <a name="definitions-and-declarations-c"></a>定義和宣告 (C++)
**Microsoft 專有**DLL 介面的所有項目 （函式和資料） 的已知在系統中，某些程式匯出，也就是宣告為的所有項目是指**dllimport**或**dllexport**. DLL 介面中的所有宣告都必須都指定**dllimport**或是**dllexport**屬性。 不過，定義必須只指定**dllexport**屬性。 例如，下列函式定義會產生編譯器錯誤：

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