---
title: 編譯器錯誤 C3293
ms.date: 07/21/2017
f1_keywords:
- C3293
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
ms.openlocfilehash: 1713632d21ef401fb1177350c81a4a64ed0503ec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760110"
---
# <a name="compiler-error-c3293"></a>編譯器錯誤 C3293

'accessor': 請用 'default' 存取類別 'type' 的預設屬性 (索引子)

不正確地存取索引屬性。  如需詳細資訊，請參閱[如何：在/cli C++中使用屬性](../../dotnet/how-to-use-properties-in-cpp-cli.md)。

**Visual Studio 2017 和更新版本**：在 Visual Studio 2015 和更早版本中，在某些情況下，編譯器會錯誤識別預設屬性做為預設的索引子。 使用 "default" 識別碼存取屬性，即可解決問題。 在 C++11 中將 default 引進為關鍵字之後，因應措施本身會變成問題。 因此，在 Visual Studio 2017 中，已修正需要因應措施的 Bug，而且編譯器現在會在使用 "default" 來存取類別的預設屬性時引發錯誤。

## <a name="example"></a>範例

下列範例會在 Visual Studio 2015 和更早版本中產生 C3293。

```cpp
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
