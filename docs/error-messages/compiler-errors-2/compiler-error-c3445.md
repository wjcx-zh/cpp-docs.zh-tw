---
title: 編譯器錯誤 C3445 |Microsoft 文件
ms.custom: ''
ms.date: 04/10/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3445
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c37f04b907183b883772fd144ae0179683f088f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256762"
---
# <a name="compiler-error-c3445"></a>編譯器錯誤 C3445

> 複本集的清單初始化 '*類型*' 不能使用明確的建構函式

根據 ISO C + + 17 標準，編譯器需要考慮複製清單初始化中的多載解析的明確建構函式，但如果實際上選擇該多載，則必須引發錯誤。

從 Visual Studio 2017 開始，編譯器會尋找使用初始設定式清單的物件建立相關的錯誤，找不到 Visual Studio 2015。 這些錯誤可能會導致損毀或未定義的行為在執行階段。

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

若要更正錯誤，請改用直接初始化：

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
