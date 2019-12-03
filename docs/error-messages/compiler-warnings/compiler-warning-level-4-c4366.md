---
title: 編譯器警告 (層級 4) C4366
ms.date: 11/04/2016
f1_keywords:
- C4366
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
ms.openlocfilehash: 18045377210b6c020786ad2ec2e003d0e764e4b5
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683267"
---
# <a name="compiler-warning-level-4-c4366"></a>編譯器警告 (層級 4) C4366

一元 ' operator ' 運算子的結果可能不對齊

如果結構成員因封裝而無法對齊，編譯器會在將該成員的位址指派給對齊的指標時發出警告。 根據預設，所有指標都會對齊。

若要解決 C4366，請變更結構的對齊方式，或使用[__unaligned](../../cpp/unaligned.md)關鍵字來宣告指標。

如需詳細資訊，請參閱 __unaligned 和[套件](../../preprocessor/pack.md)。

## <a name="example"></a>範例

下列範例會產生 C4366。

```cpp
// C4366.cpp
// compile with: /W4 /c
// processor: IPF x64
#pragma pack(1)
struct X {
   short s1;
   int s2;
};

int main() {
   X x;
   short * ps1 = &x.s1;   // OK
   int * ps2 = &x.s2;   // C4366
}
```