---
title: 遺漏函式主體或變數
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 5e3436054d69da7fb67c240c1d684585734635c3
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857150"
---
# <a name="missing-function-body-or-variable"></a>遺漏函式主體或變數

只以函式的原型，編譯器可以繼續而沒有錯誤，但連結器無法解析位址的呼叫，因為沒有任何函式程式碼或保留的變數空間。 建立連結器必須解析函式的呼叫之前，將不會看到此錯誤。

## <a name="example"></a>範例

在 main 函式呼叫會造成 LNK2019，因為原型，可讓編譯器將函式存在。  連結器會尋找它不會。

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>範例

在C++，請確定您在類別定義中包含的類別，並不只是原型的特定函式的實作。 如果您正在定義的類別標頭檔之外，務必要包含的函式之前的類別名稱 (`Classname::memberfunction`)。

```cpp
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