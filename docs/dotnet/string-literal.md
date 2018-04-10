---
title: 字串常值 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- string literals
- strings [C++], string literals
ms.assetid: 6d1fc3f8-0d58-4d68-9678-16b4f6dc4766
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dd62f85b87473d1371daf2d2fa009d8620e59b57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="string-literal"></a>字串常值
字串常值的處理已從 Managed Extensions for c + + Visual c + +。  
  
 受管理的字串常值指出引用字串常值與在 Managed Extensions for c + + 語言的設計， `S`。 例如:   
  
```  
String *ps1 = "hello";  
String *ps2 = S"goodbye";  
```  
  
 之間的效能負荷兩個初始產品為非簡單式，為下列 CIL 表示法會示範所見**ildasm**:  
  
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
  
 使用了省事只要記住 （或學習） 常值字串的前置詞`S`。 在新語法中，字串常值的處理是由透明，取決於使用的內容。 `S`不再需要指定。  
  
 什麼情況下，我們需要明確地將導向到一個解譯或其他編譯器嗎？ 在這些情況下，我們會套用明確轉換。 例如:   
  
```  
f( safe_cast<String^>("ABC") );  
```  
  
 此外，字串常值現在符合`String`與簡單的轉換，而非標準轉換。 雖然這不像許多變更的多載函式集合，其中包括解析`String`和`const char*`做為競爭的型式參數。 一次解析成的解析度`const char*`執行個體現在會標示為模糊不清。 例如:   
  
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
  
 為什麼會有差異？ 名為多個執行個體之後`f`存在在程式中，這需要套用至呼叫的函式多載解析演算法。 多載函式的型式解析牽涉到三個步驟。  
  
1.  候選函式的集合。 候選函式是這些方法的範圍內語彙上符合要叫用函數的名稱。 例如，因為`f()`叫用的執行個體透過`R`，則所有名為函式`f`所沒有的成員`R`（或其基底類別階層架構） 不是候選函式。 在本例中，有兩個候選函式。 這些是兩個成員函式的`R`名為`f`。 如果候選函式是空的則此階段中呼叫會失敗。  
  
2.  一組候選函式的可行函式。 可行的函式是可以在呼叫中，指定數目的引數和其類型的引數叫用。 在本例中，這兩個候選函式也是可行的函式。 呼叫會在這個階段期間，如果 set 可行函式是空的。  
  
3.  選取表示最符合的呼叫的函式。 這是排名的轉換套用至轉換可行函式參數的型別引數。 這是相當簡單的單一參數函式。有多個參數時，它變成較為複雜。 呼叫會在這個階段期間，如果沒有任何最符合項目。 也就是說，如果需要將實際的型式參數型別引數的類型轉換的轉換一樣理想。 呼叫會標示為模糊不清。  
  
 在 Managed Extensions，叫用此呼叫的解析度`const char*`為最佳對應的執行個體。 在新語法中，以符合需要轉換`"abc"`至`const char*`和`String^`相等現在-也就是，一樣理想的因此也就是呼叫標示成不良-為模稜兩可。  
  
 這會導致我們有兩個問題：  
  
-   什麼是實際引數的型別`"abc"`？  
  
-   判斷當一個型別轉換為於另一個更好的演算法為何？  
  
 字串常值型別`"abc"`是`const char[4]`-請記住，沒有隱含 null 結束的字元結尾的每個字串常值。  
  
 決定一個類型轉換時於另一個更好的演算法包括置於階層中的可能類型轉換。 以下是我了解該階層中的這些轉換，當然是隱含。 使用明確轉換標記法會覆寫的方式類似階層括號會覆寫運算式的一般運算子優先順序。  
  
1.  最好的完全相符。 出乎意料，如 引數完全相符，它不需要完全符合參數類型;它只必須夠接近。 這是要了解什麼進行此範例中，以及如何變更語言中的索引鍵。  
  
2.  升級是優於標準轉換。 例如，升級`short int`至`int`優於轉換`int`到`double`。  
  
3.  標準轉換是優於 boxing 轉換。 例如，轉換`int`到`double`會更好 boxing`int`到`Object`。  
  
4.  Boxing 轉換是優於隱含的使用者定義轉換。 例如，boxing`int`到`Object`優於套用的轉換運算子`SmallInt`實值類別。  
  
5.  隱含的使用者定義轉換是完全優於任何轉換。 隱含的使用者定義轉換是發生錯誤之前的最後一個結束 （但請注意，型式的簽章可能包含 param 陣列或在該位置的省略符號）。  
  
 因此，它代表什麼說出完全相符，不一定完全相符項目？ 例如，`const char[4]`不完全符合其中`const char*`或`String^`，且尚未模稜兩可的我們的範例之間兩個衝突的完全相符 ！  
  
 完全相符時，會包含一般轉換的數字。 有四個一般的轉換之下 ISO c + + 可以套用，且仍限定為完全相符。 三個統稱為左值的轉換。 第四個型別稱為 「 限定性條件轉換 」。 三個左值轉換會視為具有另一種需要限定性條件轉換較佳的完全相符。  
  
 一種形式的左值轉換為原生陣列-至指標轉換。 這是在比對中涉及的哪些項目`const char[4]`至`const char*`。 因此的相符項目`f("abc")`至`f(const char*)`完全相符。 在早期，這是語言的最佳的相符項目，執行下列事實上。  
  
 編譯器旗標的呼叫，以模稜兩可，因此，您需要的轉換`const char[4]`至`String^`也是透過一般轉換完全相符。 這是已導入新的語言版本的變更。 這就是為什麼呼叫現在標示為模糊不清。  
  
## <a name="see-also"></a>請參閱  
 [一般的語言變更 (C + + /CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [String](../windows/string-cpp-component-extensions.md)