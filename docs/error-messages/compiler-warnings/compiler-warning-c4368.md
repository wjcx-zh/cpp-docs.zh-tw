---
title: 編譯器警告 C4368
ms.date: 11/04/2016
f1_keywords:
- C4368
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
ms.openlocfilehash: d96ae14bc427568dcf7ba7bc6e5d53f3d28883ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165298"
---
# <a name="compiler-warning-c4368"></a>編譯器警告 C4368

無法將 ' member ' 定義為受控 ' type ' 的成員：不支援混合類型

您不能將原生資料成員內嵌在 CLR 型別中。

不過您可以宣告原生類型的指標，並控制指標在 Managed 類別建構函式和解構函式與完成項中的存留期。 如需詳細資訊[，請參閱析構函數和](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)完成項。

此警告一律會發出為錯誤。 請使用[warning](../../preprocessor/warning.md) pragma 來停用 C4368。

## <a name="example"></a>範例

下列範例會產生 C4368。

```cpp
// C4368.cpp
// compile with: /clr /c
struct N {};
ref struct O {};
ref struct R {
    R() : m_p( new N ) {}
    ~R() { delete m_p; }

   property N prop;   // C4368
   int i[10];   // C4368

   property O ^ prop2;   // OK
   N * m_p;   // OK
};
```
