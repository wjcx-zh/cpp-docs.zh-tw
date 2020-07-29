---
title: 編譯器警告 (層級 1) C4742
ms.date: 07/22/2020
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: e6ecd082a9f6d690414761d11d3a0adf101f87c2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233232"
---
# <a name="compiler-warning-level-1-c4742"></a>編譯器警告 (層級 1) C4742

> '*file1*' 和 '*file2*' 中的 '*variable*' 有不同的對齊方式：*數位 1*和*數位 2*

在兩個檔案中參考或定義的外部變數在這些檔案中的對齊方式不同。

## <a name="remarks"></a>備註

當編譯器發現 **`alignof`** *file1*中的變數與 **`alignof`** *file2*中的變數有不同的時，就會發出這個警告。 這可能是因為在不同的檔案中宣告變數時使用不相容的型別，或是在不同的檔案中使用不相符的類型 `#pragma pack` 。

若要解決這個警告，請使用相同的類型定義，或使用不同的變數名稱。

如需詳細資訊，請參閱 [`pack`](../../preprocessor/pack.md) and [ `alignof` 運算子](../../cpp/alignof-operator.md)。

## <a name="example"></a>範例

這是定義類型的第一個檔案。

```c
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

下列範例會產生 C4742。

```c
// C4742b.c
// compile with: C4742a.c /W1 /GL
// C4742 expected
extern struct X {
   int a;
} global;

int main() {
   global.a = 0;
}
```
