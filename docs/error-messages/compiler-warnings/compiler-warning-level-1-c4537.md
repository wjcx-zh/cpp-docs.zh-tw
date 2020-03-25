---
title: 編譯器警告 (層級 1) C4537
ms.date: 08/27/2018
f1_keywords:
- C4537
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
ms.openlocfilehash: 81058f153228d3d8fbf4097c140962d0cb9677e5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186357"
---
# <a name="compiler-warning-level-1-c4537"></a>編譯器警告 (層級 1) C4537

> '*object*'： '*operator*' 已套用至非 UDT 類型

## <a name="remarks"></a>備註

傳遞了物件（使用者定義型別）所需的參考。 參考不是物件，但是內嵌組譯工具程式碼無法進行區別。 編譯器會產生程式碼，就如同*物件*是實例一樣。

## <a name="example"></a>範例

下列範例會產生 C4537，並顯示如何修正此問題：

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
