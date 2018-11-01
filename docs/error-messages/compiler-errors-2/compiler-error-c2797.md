---
title: 編譯器錯誤 C2797
ms.date: 11/04/2016
f1_keywords:
- C2797
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
ms.openlocfilehash: 8ae8c4b8755e6f9c89c0706b0644f220761bd9c2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616230"
---
# <a name="compiler-error-c2797"></a>編譯器錯誤 C2797

（已過時）未實作成員初始設定式清單或非靜態資料成員初始設定式內的清單初始化。

這項警告是在 Visual Studio 2015 中已過時。 在 Visual Studio 2013 和舊版中，Visual c + + 編譯器不會實作成員初始設定式清單或非靜態資料成員初始設定式內的清單初始化。 在 Visual Studio 2013 Update 3 之前，這會以無訊息模式轉換成函式呼叫，這樣可能會導致產生錯誤的程式碼。 Visual Studio 2013 Update 3 將此報告為錯誤。

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