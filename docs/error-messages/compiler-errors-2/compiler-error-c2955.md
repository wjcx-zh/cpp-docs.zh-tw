---
title: 編譯器錯誤 C2955
ms.date: 03/28/2017
f1_keywords:
- C2955
helpviewer_keywords:
- C2955
ms.assetid: 77709fb6-d69b-46fd-a62f-e8564563d01b
ms.openlocfilehash: c012e5189b9ca1d0b0e786cbddacedee7c6728d2
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519993"
---
# <a name="compiler-error-c2955"></a>編譯器錯誤 C2955

'identifier': 使用類別樣板或別名泛型需要範本或泛型引數清單

若沒有範本或泛型引數清單，您無法使用類別樣板或泛型類別做為識別項。

如需詳細資訊，請參閱 <<c0> [ 類別樣板](../../cpp/class-templates.md)。

下列範例會產生 C2955，並顯示如何修正它：

```
// C2955.cpp
// compile with: /c
template<class T>
class X {};

X x1;   // C2955
X<int> x2;   // OK - this is how to fix it.
```

嘗試在類別樣板中宣告函式的行外定義時，也會發生 C2955：

```
// C2955_b.cpp
// compile with: /c
template <class T>
class CT {
public:
   void CTFunc();
   void CTFunc2();
};

void CT::CTFunc() {}   // C2955

// OK - this is how to fix it
template <class T>
void CT<T>::CTFunc2() {}
```

使用泛型時，也會發生 C2955：

```
// C2955_c.cpp
// compile with: /clr
generic <class T>
ref struct GC {
   T t;
};

int main() {
   GC^ g;   // C2955
   GC <int>^ g;
}
```

## <a name="example"></a>範例

**Visual Studio 2017 和更新版本：** 編譯器正確診斷遺漏範本引數清單時 （例如做為預設範本引數或非類型樣板參數的一部分） 的範本會出現在樣板參數清單。 下列程式碼是在 Visual Studio 2015 中編譯，但在 Visual Studio 2017 中產生錯誤。

```
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```
