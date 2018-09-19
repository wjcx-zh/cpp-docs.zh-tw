---
title: 編譯器錯誤 C3293 |Microsoft Docs
ms.custom: ''
ms.date: 07/21/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3293
dev_langs:
- C++
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d45f342528b1ee6297ee6c11a01a0eceb710595
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050329"
---
# <a name="compiler-error-c3293"></a>編譯器錯誤 C3293

'accessor': 請用 'default' 存取類別 'type' 的預設屬性 (索引子)

不正確地存取索引屬性。  請參閱[如何： 使用屬性，在 C + + /cli CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md)如需詳細資訊。

**Visual Studio 2017 和更新版本**： 在 Visual Studio 2015 和更早版本，在某些情況下，編譯器 misidentified 為預設索引子的預設屬性。 使用 "default" 識別碼存取屬性，即可解決問題。 在 C++11 中將 default 引進為關鍵字之後，因應措施本身會變成問題。 因此，在 Visual Studio 2017 中，已修正需要因應措施的 Bug，而且編譯器現在會在使用 "default" 來存取類別的預設屬性時引發錯誤。

## <a name="example"></a>範例

下列範例會產生 C3293 在 Visual Studio 2015 和更早版本。

```
// C3293.cpp
// compile with: /clr /c
using namespace System;
ref class IndexerClass {
public:
   // default indexer
   property int default[int] {
      int get(int index) { return 0; }
      void set(int index, int value) {}
   }
};

int main() {
   IndexerClass ^ ic = gcnew IndexerClass;
   ic->Item[0] = 21;   // C3293 in VS2015 OK in VS2017
   ic->default[0] = 21;   // OK in VS2015 and earlier

   String ^s = "Hello";
   wchar_t wc = s->Chars[0];   // C3293 in VS2015 OK in VS2017
   wchar_t wc2 = s->default[0];   // OK in VS2015 and earlier
   Console::WriteLine(wc2);
}
```