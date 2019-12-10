---
title: 編譯器警告 (層級 4) C4623
ms.date: 11/04/2016
f1_keywords:
- C4623
helpviewer_keywords:
- C4623
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
ms.openlocfilehash: 4d0dd9aec19fb21870a1233cd3b713337fa15aaa
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990639"
---
# <a name="compiler-warning-level-4-c4623"></a>編譯器警告 (層級 4) C4623

'`derived class`'：預設建構函式已隱含定義為刪除，因為基底類別預設建構函式無法存取或已被刪除

建構函式已無法在基底類別中存取，而無法對衍生類別產生。 在此堆疊上建立此類型物件的任何嘗試都會導致編譯器錯誤。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

## <a name="example"></a>範例

下列範例會產生 C4623。

```cpp
// C4623.cpp
// compile with: /W4
#pragma warning(default : 4623)
class B {
   B();
};

class C {
public:
   C();
};

class D : public B {};   // C4623 - to fix, make B's constructor public
class E : public C {};   // OK - class C constructor is public

int main() {
   // D d;  will cause an error
}
```
