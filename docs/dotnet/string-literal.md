---
title: 字串常值 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- string literals
- strings [C++], string literals
ms.assetid: 6d1fc3f8-0d58-4d68-9678-16b4f6dc4766
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 41f1996cd4f4caf24ac08d09b05e636cb09f7eed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415261"
---
# <a name="string-literal"></a>字串常值

字串常值的處理已從 Managed Extensions for c + + Visual c + +。

受管理的字串常值表示前面引用字串常值中使用 Managed Extensions for c + + 語言設計，在`S`。 例如: 

```
String *ps1 = "hello";
String *ps2 = S"goodbye";
```

效能額外負荷之間兩個初始化為重要的為下列的 CIL 表示法會示範所示**ildasm**:

```
// String *ps1 = "hello";
ldsflda    valuetype $ArrayType$0xd61117dd
     modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier)
     '?A0xbdde7aca.unnamed-global-0'

newobj instance void [mscorlib]System.String::.ctor(int8*)
stloc.0

// String *ps2 = S"goodbye";
ldstr      "goodbye"
stloc.0
```

這與只記住 （或學習） 為常值字串的前置詞省事`S`。 在新語法中，字串常值的處理很透明，取決於使用的內容。 `S`不再需要指定。

呢，我們需要明確的情況下會指示編譯器解譯一個或另一個嗎？ 在這些情況下，我們可以套用明確轉換。 例如: 

```
f( safe_cast<String^>("ABC") );
```

此外，字串常值現在符合`String`使用簡單的轉換，而不是標準的轉換。 雖然這聽起來不足變更的多載函式集，其中包括解析更`String`和`const char*`做為競爭的型式參數。 一次，解析為解析`const char*`執行個體現在會標示為模稜兩可。 例如: 

```
ref struct R {
   void f(const char*);
   void f(String^);
};

int main () {
   R r;
   // old syntax: f( const char* );
   // new syntax: error: ambiguous
   r.f("ABC"); 
}
```

為什麼有何差別？ 因為多個名為的執行個體`f`存在在程式中，這需要套用至呼叫的函式多載解析演算法。 多載函式的型式解析包含三個步驟。

1. 候選函式的集合。 候選函式是那些方法範圍內語彙符合要叫用函數的名稱。 比方說，因為`f()`的執行個體透過叫用`R`，則所有具名函式`f`所沒有的成員`R`（或其基底類別階層架構的） 不是候選函式。 在本例中，有兩個候選函式。 這些是兩個成員函式`R`名為`f`。 如果候選函式集是空的則在這個階段中的呼叫會失敗。

1. 基本的可行候選函式的函式集。 基本的可行的函式是可指定在呼叫中，指定的引數和其類型數目的引數叫用。 在本例中，這兩個候選函式也是可行的函式。 如果可行的函式集是空的則在這個階段中的呼叫會失敗。

1. 選取代表最符合項目呼叫的函式。 這是排名套用來轉換可行的函式參數的型別引數的轉換。 這是相當簡單的單一參數函式;有多個參數時，它會變得較為複雜。 在這個階段期間的呼叫失敗，如果沒有任何最符合項目。 也就是說，如果需要轉換的型式參數類型的實際引數類型的轉換一樣好。 呼叫會標示為模稜兩可。

受管理的擴充功能，叫用此呼叫的解析度中`const char*`為最佳的相符項目執行個體。 在新語法中，以符合所需的轉換`"abc"`要`const char*`和`String^`是現在相同-也就是，一樣好-，因此也就是呼叫標示為 bad-為模稜兩可。

這會讓我們前往 兩個問題：

- 什麼是實際的引數，類型`"abc"`？

- 判斷一個型別轉換比另一個更好的演算法為何？

字串常值的型別`"abc"`是`const char[4]`-請記住，沒有隱含 null 結束的字元結尾的每個字串常值。

決定何時優於另一個類型轉換的演算法牽涉到置於階層中的可能類型轉換。 以下是 我了解該階層-的這些所有轉換，當然都是隱含。 使用明確轉換標記法會覆寫的方式類似的階層架構的括號會覆寫運算式的一般運算子優先順序。

1. 最好的完全相符。 令人驚訝，到完全相符的引數，它不需要完全符合參數類型;它只需要為夠接近。 這是要了解發生什麼情況在本例中，以及如何變更語言的索引鍵。

1. 升級是優於標準轉換。 例如，升級`short int`要`int`優於轉換`int`成`double`。

1. 標準轉換是優於 boxing 轉換。 例如，將轉換`int`成`double`會更好 boxing`int`成`Object`。

1. Boxing 轉換是優於的使用者定義的隱含轉換。 比方說，boxing`int`成`Object`優於套用的轉換運算子`SmallInt`實值類別。

1. 使用者定義的隱含轉換是完全比任何轉換更好。 使用者定義的隱含轉換為錯誤之前的最後一個結束 （含警告型式的簽章可能包含的 param 陣列或該位置的省略符號）。

因此，什麼意思到完全相符，不一定完全相符項目？ 例如，`const char[4]`完全符合其中一個`const char*`或`String^`，還有兩個衝突完全相符項目之間就是我們的範例中的模稜兩可和 ！

完全相符時，會包含一般轉換的數字。 有四個一般的轉換之下 ISO-C + + 可以套用，且仍限定為完全相符。 三個統稱為左值轉換。 第四個型別稱為 「 限定性條件轉換 」。 三個 「 左值 」 轉換會視為比另一種需要限定性條件轉換更好的完全相符。

一種形式的左值轉換為原生陣列-至-指標轉換。 這是在比對中的相關`const char[4]`至`const char*`。 因此的相符項目`f("abc")`至`f(const char*)`完全相符。 在早期的我們中，這是語言的最佳的相符項目，執行下列事實上。

讓編譯器旗標呼叫為模稜兩可，因此，需要的轉換`const char[4]`至`String^`也是透過一般轉換完全相符。 這是新的語言版本中已引進的變更。 這就是為什麼呼叫現在會標示為模稜兩可。

## <a name="see-also"></a>另請參閱

[一般的語言變更 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[String](../windows/string-cpp-component-extensions.md)