---
title: 編譯器警告 (層級 1) C4537
ms.date: 08/27/2018
f1_keywords:
- C4537
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
ms.openlocfilehash: 2f97be4e1aaa5143df685cb95935d350e6f02534
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441311"
---
# <a name="compiler-warning-level-1-c4537"></a>編譯器警告 (層級 1) C4537

> '*物件*':'*運算子*' 套用至非 UDT 類型

## <a name="remarks"></a>備註

參考已傳遞的物件 （使用者定義型別） 需要的地方。 參考不是一個物件，但內嵌組合語言程式碼不能夠做出區別。 編譯器會產生程式碼，不過*物件*已執行個體。

## <a name="example"></a>範例

下列範例會產生 C4537，並示範如何修正此問題：

```cpp
// C4537.cpp
// compile with: /W1 /c
// processor: x86
struct S {
    int member;
};

void f1(S &s) {
    __asm mov eax, s.member;   // C4537
    // try the following code instead
    // or, make the declaration "void f1(S s)"
    /*
    mov eax, s
    mov eax, [eax]s.member
    */
}
```