---
title: "編譯器錯誤 C2653 |Microsoft 文件"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2653
dev_langs:
- C++
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f18e3d6210c5d9b9aba4fdfaab296a01d32b6d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2653"></a>編譯器錯誤 C2653

> '*識別碼*': 不是類別或命名空間名稱

語言語法需要類別、 結構、 等位或在此命名空間名稱。

當您使用尚未宣告為類別、 結構、 等位或命名空間範圍運算子前方的名稱時，會發生此錯誤。 若要修正此問題，宣告名稱，或包含宣告的名稱，才能使用的標頭。

您也可以，如果您嘗試定義 C2653*複合命名空間*，包含一或多個範圍巢狀命名空間名稱的命名空間。 複合定義中不允許使用 c + + 在 C + + 17 之前的命名空間。 當您指定時，在 Visual Studio 2015 Update 3 開始支援複合的命名空間[/std:c + + 最新](../../build/reference/std-specify-language-standard-version.md)編譯器選項。 從 Visual c + + 2017 15.5 版本開始，編譯器支援複合的命名空間定義當[/std:c + + 17](../../build/reference/std-specify-language-standard-version.md)指定選項。

## <a name="examples"></a>範例

這個範例會產生 C2653，因為已使用的領域名稱，但未宣告。 編譯器會預期類別、 結構、 等位或之前的範圍運算子 （:） 的命名空間名稱。

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

在未編譯 C + + 17 或更新版本標準的程式碼，巢狀命名空間必須使用每個巢狀層級的明確命名空間宣告：

```cpp
// C2653b.cpp
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,
                          // C2429 thereafter. Use /std:c++17 or /std:c++latest to fix.

namespace a {             // Use this form for compliant code under /std:c++14 (the default)
   namespace b {          // or when using compilers before Visual Studio 2015 update 3.
      int i;
   }
}

int main() {
   a::b::i = 2;
}
```
