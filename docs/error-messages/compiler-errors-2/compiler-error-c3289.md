---
title: 編譯器錯誤 C3289 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3289
dev_langs:
- C++
helpviewer_keywords:
- C3289
ms.assetid: 3c1c623b-7fcf-43ab-a89a-8722532a8d29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 185fc7d70a9510ce9caf252398b63dd3c59c1f7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020208"
---
# <a name="compiler-error-c3289"></a>編譯器錯誤 C3289

'property' : trivial 屬性不可索引

屬性宣告不正確。 必須定義索引屬性的存取子。 如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md) 。

## <a name="example"></a>範例

下列範例會產生 C3289。

```
// C3289.cpp
// compile with: /clr
public ref struct C {
   // user-defined simple indexer
   property int indexer1[int];   // C3289

   // user-defined indexer
   property int indexer2[int] {
      int get(int i) { return 0; }
      void set(int i, int j) {}
   }
};

int main() {
   C ^ MyC = gcnew C();
   MyC->indexer2[0] = 1;
}
```