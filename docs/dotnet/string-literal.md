---
title: "字串常值 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字串常值"
  - "字串 [C++], 字串常值"
ms.assetid: 6d1fc3f8-0d58-4d68-9678-16b4f6dc4766
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 字串常值
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，字串常值的處理方式已變更。  
  
 在 Managed Extensions for C\+\+ 語言設計中，會以字串常值前面加上 `S` 表示 Managed 字串常值。  例如：  
  
```  
String *ps1 = "hello";  
String *ps2 = S"goodbye";  
```  
  
 兩個初始化之間的效能負荷會變成非一般性，如下列 CIL 表示透過 **ildasm** 的示範所示：  
  
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
  
 只要記得 \(或學會\) 在字串常值前面加上 `S` 就極為省事。  在新語法中，字串常值的處理很透明，是由使用內容所決定。  不再需要指定 `S`。  
  
 在什麼情況下需要明確地將編譯器導向某項解譯或另一項解譯？  在這些情況下，都會套用明確轉換。  例如：  
  
```  
f( safe_cast<String^>("ABC") );  
```  
  
 此外，字串常值現在會用簡易轉換而非標準轉換來比對 `String`。  雖然這聽起來不太像，但是它會變更多載函式集 \(Function Set\) 的解析，而此多載函式集內含 `String` 和 `const char*` 做為競爭性型式參數。  解析一旦解析為 `const char*` 執行個體，現在就會標示為模稜兩可。  例如：  
  
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
  
 為什麼產生差異？  由於程式中有多個名為 `f` 的執行個體，因此會要求將函式多載解析演算法套用至呼叫。  多載函式的型式解析包含三個步驟。  
  
1.  候選函式的集合。  當方法處於語彙上符合所叫用函式之名稱的範圍時，就算是候選函式。  例如，由於是透過 `R` 的執行個體叫用 `f()`，因此非 `R` \(或基底類別階層\) 成員的所有已命名函式 `f` 就不是候選函式。  在我們的範例中有兩個候選函式。  亦即 `R` 的兩個成員函式，而且名為 `f`。  如果候選函式集是空的，則此階段中的呼叫會失敗。  
  
2.  候選函式中的可行函式集。  當函式可以使用呼叫中所指定的引數叫用，並且給定引數數目和引數型別，則為可行函式。  在我們範例中的那兩個候選函式都是可行函式。  如果可行函式集是空的，則此階段中的呼叫會失敗。  
  
3.  選取表示呼叫最符合項目的函式。  排列所套用轉換的等級，將引數轉換為可行函式參數的型別，以達到此目的。  當函式只有單一參數時，情況非常簡單；但是當有多個參數時，或多或少會比較複雜。  如果缺少最符合項目，則此階段中的呼叫會失敗。  也就是，如果要將實際引數的型別轉換為型式參數的型別時所需的轉換很正確時。  呼叫會標示為模棱兩可。  
  
 在 Managed Extensions 中，此呼叫的解析會叫用 `const char*` 執行個體當做最符合項目。  在新語法中，使 `"abc"` 與 `const char*` 和 `String^` 相符的必要轉換已是對等 \(也就是很正確\)，因此呼叫會標示為不正確 \(也就是模稜兩可\)。  
  
 這會衍伸兩個問題：  
  
-   實際引數 `"abc"` 的型別為何？  
  
-   可以使用什麼演算法判定某種型別轉換優於另一種型別轉換？  
  
 字串常值 `"abc"` 的型別為 `const char[4]`；請記住，每個字串常值的末端都有隱含的 null 結尾字元。  
  
 用來判定某種型別轉換優於另一種型別轉換的演算法，會將所有可能的型別轉換都放在階層上。  就我對該階層的了解而言，所有這些轉換理當都是隱含的。  使用明確轉換標記法覆寫階層的方式，類似於括弧覆寫運算式的一般運算子優先順序 \(Operator Precedence\)。  
  
1.  完全相符最好。  令人訝異的是，若要引數完全相符，並不需要明確地符合參數型別，只要夠相似就好了。  這是了解本範例如何運作以及語言如何變更的關鍵。  
  
2.  提升優於標準轉換。  例如，將 `short int` 提升至 `int` 比將 `int` 轉換為 `double` 來的好。  
  
3.  標準轉換優於 Boxing 轉換。  例如，將 `int` 轉換為 `double` 比將 `int` 裝到 `Object` 型別的容器來的好。  
  
4.  Boxing 轉換優於隱含的使用者定義轉換。  例如，將 `int` Box 處理為 `Object` 比套用 `SmallInt` 實值類別的轉換運算子來的好。  
  
5.  隱含的使用者定義轉換優於完全不做轉換。  隱含的使用者定義轉換是錯誤之前的最後結束 \(附帶一項警告，型式簽章可能在那個位置上包含 param 陣列或省略\)。  
  
 那麼，完全相符不必一定要是相符項目，這句話是什麼意思？  例如，`const char[4]` 無法完全符合 `const char*` 或 `String^`，但是範例的模稜兩可介於兩個衝突的完全相符之間！  
  
 發生完全相符時，會包含一些一般轉換。  在 ISO\-C\+\+ 底下有四種可以套用，且仍限定為完全相符的一般轉換。  前三種稱為左值轉換。  第四種型別稱為限定性條件轉換。  此三種左值轉換與另一種需要限定性條件轉換比較，是被視為具有較佳的完全相符。  
  
 原生陣列至指標轉換屬於左值轉換的一種形式。  這是將 `const char[4]` 比對 `const char*` 時所做的工作。  因此，將 `f("abc")` 比對 `f(const char*)` 為完全相符。  在早期的語言中，這實際上是最佳相符。  
  
 編譯器要將呼叫標示為模棱兩可，因此會要求 `const char[4]` 至 `String^` 的轉換也要是透過一般轉換的完全相符。  這是已引入新語言版本中的變更。  而且這也是現在呼叫標示為模棱兩可的原因。  
  
## 請參閱  
 [一般的語言變更](../dotnet/general-language-changes-cpp-cli.md)   
 [String](../windows/string-cpp-component-extensions.md)