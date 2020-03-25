---
title: 編譯器錯誤 C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: 0cbcf7dc80aedc554594f88992059f98b7091c21
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201628"
---
# <a name="compiler-error-c2868"></a>編譯器錯誤 C2868

> '*identifier*'：使用-宣告的語法不合法;預期的限定名稱

[Using](../../cpp/using-declaration.md)宣告需要*限定名稱*、以範圍運算子（`::`）分隔的命名空間、類別或列舉名稱的序列（以識別碼名稱結尾）。 單一範圍解析運算子可用來引入全域命名空間中的名稱。

## <a name="example"></a>範例

下列範例會產生 C2868，而且也會顯示正確的使用方式：

```cpp
// C2868.cpp
class X {
public:
   int i;
};

class Y : X {
public:
   using X::i;   // OK
};

int main() {
   using X;   // C2868
}
```
