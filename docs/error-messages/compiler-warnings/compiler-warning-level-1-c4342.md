---
title: 編譯器警告 (層級 1) C4342
ms.date: 11/04/2016
f1_keywords:
- C4342
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
ms.openlocfilehash: 8ac00d3d57f8cf7d6c85f3106dbe9b8c3cb9adf0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162916"
---
# <a name="compiler-warning-level-1-c4342"></a>編譯器警告 (層級 1) C4342

行為變更：呼叫了 '*function*'，但在先前的版本中呼叫了成員運算子

在 Visual Studio 2002 之前C++的 Visual 版本中，已呼叫成員，但此行為已變更，而且編譯器現在會在命名空間範圍中尋找最符合的值。

如果找到成員運算子，編譯器先前不會考慮任何命名空間範圍運算子。 如果命名空間範圍較相符，則目前的編譯器會正確地呼叫它，而先前的編譯器不會將它視為。

當您成功地將程式碼移植到目前的版本之後，應該停用此警告。  編譯器可能會產生誤報，針對沒有行為變更的程式碼產生此警告。

此警告預設為關閉。 如需詳細資訊，請參閱 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

下列範例會產生 C4342：

```cpp
// C4342.cpp
// compile with: /EHsc /W1
#include <fstream>
#pragma warning(default: 4342)
using namespace std;
struct X : public ofstream {
   X();
};

X::X() {
   open( "ofs_bug_ev.txt." );
   if ( is_open() ) {
      *this << "Text" << "<-should be text" << endl;   // C4342
      *this << ' ' << "<-should be space symbol" << endl;   // C4342
   }
}

int main() {
   X b;
   b << "Text" << "<-should be text" << endl;
   b << ' ' << "<-should be space symbol" << endl;
}
```
