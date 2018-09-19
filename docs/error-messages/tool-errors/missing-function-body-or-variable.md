---
title: 遺漏函式主體或變數 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a1337cf936d986c038aacc355490f13e5f0c2d8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088445"
---
# <a name="missing-function-body-or-variable"></a>遺漏函式主體或變數

只以函式的原型，編譯器可以繼續而沒有錯誤，但連結器無法解析位址的呼叫，因為沒有任何函式程式碼或保留的變數空間。 建立連結器必須解析函式的呼叫之前，將不會看到此錯誤。

## <a name="example"></a>範例

在 main 函式呼叫會造成 LNK2019，因為原型，可讓編譯器將函式存在。  連結器會尋找它不會。

```
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>範例

在 c + +，請確定您在類別定義中包含的類別，並不只是原型的特定函式的實作。 如果您正在定義的類別標頭檔之外，務必要包含的函式之前的類別名稱 (`Classname::memberfunction`)。

```
// LNK2019_MFBV_2.cpp
// LNK2019 expected
struct A {
   static void Test();
};

// Should be void A::Test() {}
void Test() {}

int main() {
   A AObject;
   AObject.Test();
}
```

## <a name="see-also"></a>另請參閱

[連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)