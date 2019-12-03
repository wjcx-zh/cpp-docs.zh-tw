---
title: 編譯器警告 (層級 4) C4339
ms.date: 11/04/2016
f1_keywords:
- C4339
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
ms.openlocfilehash: fffdaa255f6b8f2259488df610f163bebf8d6dec
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683298"
---
# <a name="compiler-warning-level-4-c4339"></a>編譯器警告 (層級 4) C4339

'type'：偵測到在 WinRT 或 CLR 中繼資料中使用未定義的類型 - 使用此類型可能造成執行階段例外狀況

未在 Windows 執行階段或 Common Language Runtime 編譯的程式碼中定義類型。 定義要避免可能的執行階段例外狀況的類型。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

下列範例會產生 C4339，並示範如何修正此問題：

```cpp
// C4339.cpp
// compile with: /W4 /clr /c
// C4339 expected
#pragma warning(default : 4339)

// Delete the following line to resolve.
class A;

// Uncomment the following line to resolve.
// class A{};

class X {
public:
   X() {}

   virtual A *mf() {
      return 0;
   }
};

X * f() {
   return new X();
}
```