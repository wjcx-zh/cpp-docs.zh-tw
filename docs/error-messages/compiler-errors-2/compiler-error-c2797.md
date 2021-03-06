---
title: 編譯器錯誤 C2797
ms.date: 11/04/2016
f1_keywords:
- C2797
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
ms.openlocfilehash: 9973ddcccc69e85bdf79e0623fa4bcc1d6689032
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202071"
---
# <a name="compiler-error-c2797"></a>編譯器錯誤 C2797

過時不會實作為成員初始化運算式清單或非靜態資料成員初始化運算式中的清單初始設定。

此警告在 Visual Studio 2015 中已過時。 在 Visual Studio 2013 和較舊版本中， C++ Microsoft 編譯器不會在成員初始化運算式清單或非靜態資料成員初始化運算式內，執行清單初始化。 在 Visual Studio 2013 Update 3 之前，這會以無訊息模式轉換成函式呼叫，這樣可能會導致產生錯誤的程式碼。 Visual Studio 2013 Update 3 將此報告為錯誤。

本範例會產生 C2797：

```
#include <vector>
struct S {
    S() : v1{1} {} // C2797, VS2013 RTM incorrectly calls 'vector(size_type)'

    std::vector<int> v1;
    std::vector<int> v2{1, 2}; // C2797, VS2013 RTM incorrectly calls 'vector(size_type, const int &)'
};
```

本範例也會產生 C2797：

```
struct S1 {
    int i;
};

struct S2 {
    S2() : s1{0} {} // C2797, VS2013 RTM interprets as S2() : s1(0) {} causing C2664
    S1 s1;
    S1 s2{0}; // C2797, VS2013 RTM interprets as S1 s2 = S1(0); causing C2664
};
```

若要修正這個問題，您可以使用內部清單的明確建構。 例如：

```
#include <vector>
typedef std::vector<int> Vector;
struct S {
    S() : v1(Vector{1}) {}

    Vector v1;
    Vector v2 = Vector{1, 2};
};
```

如果您不需要清單初始設定：

```
struct S {
    S() : s1("") {}

    std::string s1;
    std::string s2 = std::string("");
};
```

(Visual Studio 2013 中的編譯器會在 Visual Studio 2013 Update 3 之前隱含地執行此操作。)
