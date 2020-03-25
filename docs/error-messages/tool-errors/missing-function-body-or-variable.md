---
title: 遺漏函式主體或變數
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 6d2ef22b90009d320485fb6fe3f7e308ae05c442
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173617"
---
# <a name="missing-function-body-or-variable"></a>遺漏函式主體或變數

只要使用函式原型，編譯器就可以繼續執行而不會發生錯誤，但連結器無法解析位址的呼叫，因為沒有任何函式程式碼或變數空間保留。 在您建立連結器必須解析的函式呼叫之前，不會看到這個錯誤。

## <a name="example"></a>範例

Main 中的函式呼叫會造成 LNK2019，因為原型允許編譯器將函式視為存在。  連結器發現它不是。

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>範例

在C++中，請確定您包含類別的特定函式的實作為，而不只是類別定義中的原型。 如果您要在標頭檔外部定義類別，請務必在函式（`Classname::memberfunction`）前面包含類別名稱。

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
