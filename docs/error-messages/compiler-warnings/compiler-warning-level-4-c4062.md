---
title: 編譯器警告 (層級 4) C4062
ms.date: 04/05/2019
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: 79658afc31565b708cdbd8a88f49b887cdd10cf3
ms.sourcegitcommit: 35c4b3478f8cc310ebbd932a18963ad8ab846ed9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59237181"
---
# <a name="compiler-warning-level-4-c4062"></a>編譯器警告 (層級 4) C4062

> 列舉值 '*識別碼*'參數中的列舉'*列舉*' 未處理

列舉值*識別碼*沒有相關聯的任何`case`中的處理常式`switch`陳述式，而且沒有任何`default`可以進行攔截的標籤。 遺失的情況下可能會疏忽，，而且是在程式碼中潛在的錯誤。 未使用的列舉值中的相關警告`switch`有陳述式`default`情況下，請參閱[C4061](compiler-warning-level-4-c4061.md)。

此警告預設為關閉。 如需如何啟用預設為關閉的警告的詳細資訊，請參閱[編譯器警告，預設為關閉的](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

## <a name="example"></a>範例

下列範例會產生 C4062，，並示範如何修正此問題：

```cpp
// C4062.cpp
// compile with: /EHsc /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
   // case c:  // to fix, uncomment this line
      break;   // no default label
   }   // C4062, enumerator 'c' not handled
}

int main() {
}
```

## <a name="see-also"></a>另請參閱

[編譯器警告 （層級 4） C4061](compiler-warning-level-4-c4061.md)
