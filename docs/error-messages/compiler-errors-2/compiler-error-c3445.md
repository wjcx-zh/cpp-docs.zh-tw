---
title: 編譯器錯誤 C3445
ms.date: 04/10/2017
f1_keywords:
- C3445
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
ms.openlocfilehash: 2eddeb5a56c953ca0864e29187fbe28c53bdee24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574209"
---
# <a name="compiler-error-c3445"></a>編譯器錯誤 C3445

> 複製-清單初始化的 '*型別*' 不能使用明確的建構函式

根據 ISO c++17 標準，編譯器需要考慮複製清單初始化中的多載解析的明確建構函式，但必須在實際選擇該多載時引發錯誤。

從 Visual Studio 2017 中，編譯器會尋找使用初始設定式清單建立物件相關的錯誤，找不到 Visual Studio 2015。 這些錯誤可能會導致當機或未定義的行為，在執行階段。

## <a name="example"></a>範例

下列範例會產生 C3445。

```cpp
// C3445.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of
                      //     'A' cannot use an explicit constructor
}
```

若要更正錯誤，請改為使用直接初始化：

```cpp
// C3445b.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1{ 1 };
}
```
