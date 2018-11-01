---
title: 編譯器錯誤 C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: 4cb259ed0f43831226fb7e1a1ccf7b28bcef7819
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614769"
---
# <a name="compiler-error-c2868"></a>編譯器錯誤 C2868

> '*識別碼*': using 宣告不合法語法; 預期的限定名稱

A [using 宣告](../../cpp/using-declaration.md)需要*限定的名稱*，範圍運算子 (`::`) 分隔的命名空間、 類別或列舉的名稱結尾的識別項名稱的序列。 單一的範圍解析運算子可用來從全域命名空間引入名稱使用。

## <a name="example"></a>範例

下列範例會產生 C2868，並也會示範正確使用方式：

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