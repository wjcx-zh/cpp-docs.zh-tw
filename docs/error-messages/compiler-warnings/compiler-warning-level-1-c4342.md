---
title: 編譯器警告 (層級 1) C4342
ms.date: 11/04/2016
f1_keywords:
- C4342
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
ms.openlocfilehash: 439c4976f25688fd9220c3f58ceb933266b5f15c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447330"
---
# <a name="compiler-warning-level-1-c4342"></a>編譯器警告 (層級 1) C4342

行為變更: '*函式*' 呼叫，但在舊版中呼叫成員運算子

在 Visual Studio 2002 之前的 Visual c + + 版本中，呼叫成員時，此行為已變更但編譯器現在會找出最符合項目命名空間範圍中。

如果找不到成員運算子，編譯器之前不會考慮任何命名空間範圍運算子。 如果沒有更好的相符項目，在命名空間範圍，目前的編譯器正確呼叫它，而舊版編譯器不會考慮。

在您成功地移植程式碼，以最新版本之後，應該停用此警告。  編譯器可能會產生誤判，產生這個警告的程式碼沒有任何行為變更。

此警告預設為關閉。 如需詳細資訊，請參閱 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

下列範例會產生 C4342:

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