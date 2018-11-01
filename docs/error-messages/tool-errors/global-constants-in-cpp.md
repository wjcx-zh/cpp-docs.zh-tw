---
title: C++ 的全域常數
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: 3da61b7718dadba9b454ee079651ce6372f21756
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432613"
---
# <a name="global-constants-in-c"></a>C++ 的全域常數

C + + 的全域常數有靜態連結。 這是不同於 c。如果您嘗試使用全域常數 c + + 中多個檔案，就會發生無法解析的外部錯誤。 編譯器最佳化全域常數，沒有留下保留給變數。

若要解決此錯誤的一個方式是標頭檔中包含常數的初始化，並在必要時，就如同它是函式原型 CPP 檔案中包含該標頭。 另一個可能性是將變數設為非常數，並使用常數的參考，評估它。

下列範例會產生 C2019:

```
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

然後，

```
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>另請參閱

[連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)