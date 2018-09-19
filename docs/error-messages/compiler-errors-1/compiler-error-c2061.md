---
title: 編譯器錯誤 C2061 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2061
dev_langs:
- C++
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 896fdb21c57e0f558b87ec23e2be309cf49f8095
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057960"
---
# <a name="compiler-error-c2061"></a>編譯器錯誤 C2061

語法錯誤： 識別項 'identifier'

編譯器發現之識別項，它不預期的位置。 請確定`identifier`宣告才能使用它。

初始設定式可能會以括號括住。 若要避免這個問題，括號括住宣告子，或使它`typedef`。

當編譯器偵測到的運算式做為類別範本引數; 也會發生此錯誤使用  [typename](../../cpp/typename.md)告訴編譯器為型別。

下列範例會產生 C2061:

```
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

如果您傳遞至執行個體名稱，就會發生 C2061 [typeid](../../windows/typeid-cpp-component-extensions.md):

```
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```