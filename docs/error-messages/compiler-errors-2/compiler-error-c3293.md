---
title: 編譯器錯誤 C3293
ms.date: 07/21/2017
f1_keywords:
- C3293
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
ms.openlocfilehash: 84d539722474d5f5dfffe1f6fe121bb7349ba131
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548200"
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