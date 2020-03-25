---
title: 編譯器警告 (層級 1) C4376
ms.date: 11/04/2016
f1_keywords:
- C4376
helpviewer_keywords:
- C4376
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
ms.openlocfilehash: 8009d2e5d09ad173f6150ebe9a907be9f4947cd7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162852"
---
# <a name="compiler-warning-level-1-c4376"></a>編譯器警告 (層級 1) C4376

已不再支援存取規範 ' old_specifier： '：請改用 ' new_specifier： '

如需在中繼資料中指定類型和成員存取範圍的詳細資訊，請參閱[如何：定義和使用類別和結構（C++/cli）](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)中的[類型可見度](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)和[成員可見度](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility)。

## <a name="example"></a>範例

下列範例會產生 C4376。

```cpp
// C4376.cpp
// compile with: /clr /W1 /c
public ref class G {
public public:   // C4376
   void m2();
};

public ref class H {
public:   // OK
   void m2();
};
```
