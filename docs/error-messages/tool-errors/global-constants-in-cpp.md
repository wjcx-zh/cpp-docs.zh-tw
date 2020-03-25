---
title: C++ 的全域常數
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: cabe5e92a496181d60536d7274eca388aba5c068
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195470"
---
# <a name="global-constants-in-c"></a>C++ 的全域常數

C++全域常數具有靜態連結。 這與 C 不同。如果您嘗試在多個檔案中使用C++全域常數，則會收到無法解析的外部錯誤。 編譯器會將全域常數優化，而不會保留變數的任何空間。

解決這個錯誤的其中一種方法是在標頭檔中包含 const 初始化，並在必要時將該標頭包含在 CPP 檔案中，就像是函式原型一樣。 另一個可能性是將變數設為非常數，並在進行評估時使用常數參考。

下列範例會產生 C2019：

```cpp
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

然後，

```cpp
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>另請參閱

[連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
