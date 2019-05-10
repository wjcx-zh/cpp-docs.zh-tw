---
title: C++ 的全域常數
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: 2f0621f52fe445f8f2058ef902824ddc1f5e2bb5
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64856111"
---
# <a name="global-constants-in-c"></a>C++ 的全域常數

C++全域常數有靜態連結。 這是不同於 c。如果您嘗試使用中的全域常數C++在多個檔案中，您收到無法解析的外部錯誤。 編譯器最佳化全域常數，沒有留下保留給變數。

若要解決此錯誤的一個方式是標頭檔中包含常數的初始化，並在必要時，就如同它是函式原型 CPP 檔案中包含該標頭。 另一個可能性是將變數設為非常數，並使用常數的參考，評估它。

下列範例會產生 C2019:

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