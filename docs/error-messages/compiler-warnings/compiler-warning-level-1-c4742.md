---
title: 編譯器警告（層級1） C4742
ms.date: 11/04/2016
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: 11663a9b8672e2f91feb59e275181dbe645484e9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051301"
---
# <a name="compiler-warning-level-1-c4742"></a>編譯器警告（層級1） C4742

' var ' 在 ' file1 ' 和 ' file2 ' 中有不同的對齊方式：數位和數位

在兩個檔案中參考或定義的外部變數在這些檔案中的對齊方式不同。 當編譯器發現*file1*中變數的 `__alignof` 與*file2*中變數的 `__alignof` 不同時，就會發出此警告。 這可能是因為在不同的檔案中宣告變數時使用不相容的類型，或是在不同的檔案中使用不相符的 `#pragma pack` 所造成。

若要解決這個警告，請使用相同的類型定義，或使用不同的變數名稱。

如需詳細資訊，請參閱[pack](../../preprocessor/pack.md)和[__alignof 運算子](../../cpp/alignof-operator.md)。

## <a name="example"></a>範例

這是定義類型的第一個檔案。

```c
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

## <a name="example"></a>範例

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