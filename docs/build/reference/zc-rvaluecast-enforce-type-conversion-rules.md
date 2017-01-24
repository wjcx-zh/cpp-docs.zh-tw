---
title: "/Zc:rvalueCast (強制型別轉換規則) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "rvaluecast"
  - "/Zc:rvalueCast"
  - "VC.Project.VCCLCompilerTool.EnforceTypeConversionRules"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc 編譯器選項 (C++)"
  - "強制型別轉換規則"
  - "rvaluecast"
  - "Zc 編譯器選項 (C++)"
  - "-Zc 編譯器選項 (C++)"
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zc:rvalueCast (強制型別轉換規則)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當指定 **\/Zc:rvalueCast** 選項時，編譯器會依照 C\+\+11 標準，正確地將右值參考類型識別為轉型作業的結果。  當未指定該選項時，編譯器的行為會與 Visual Studio 2012 中的行為相同。  根據預設，**\/Zc:rvalueCast** 為關閉。  為了取得一致性，並消除使用轉型中的錯誤，建議您使用 **\/Zc:rvalueCast**。  
  
## 語法  
  
```  
/Zc:rvalueCast[-]  
```  
  
## 備註  
 如果指定 **\/Zc:rvalueCast**，則編譯器會遵循 C\+\+11 標準的 5.4 節，並僅將導致非參考類型的轉型運算式和導致非函式類型右值參考的轉型運算式，視為右值類型。  根據預設，或者如果指定 **\/Zc:rvalueCast\-**，則編譯器會不一致，且會將導致右值參考的所有轉型運算式，視為右值。  
  
 如果您將轉型運算式作為引數，傳遞至採用右值參考類型的函式，請使用 **\/Zc:rvalueCast**。  當編譯器錯誤地判定轉型運算式的類型時，預設行為會導致編譯器錯誤 [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md)。  此範例顯示未指定 \/Zc:rvalueCast 時，正確程式碼中的編譯器錯誤。  
  
```cpp  
// Test of /Zc:rvalueCast  
// compile by using:  
// cl /c /Zc:rvalueCast- make_thing.cpp  
// cl /c /Zc:rvalueCast make_thing.cpp  
  
#include <utility>  
  
template <typename T>   
struct Thing {  
   // Construct a Thing by using two rvalue reference parameters  
   Thing(T&& t1, T&& t2)  
      : thing1(t1), thing2(t2) {}  
  
   T& thing1;  
   T& thing2;  
};  
  
// Create a Thing, using move semantics if possible  
template <typename T>  
Thing<T> make_thing(T&& t1, T&& t2)  
{  
   return (Thing<T>(std::forward<T>(t1), std::forward<T>(t2)));  
}  
  
struct Test1 {  
   long a;  
   long b;  
  
   Thing<long> test() {   
      // Use identity casts to create rvalues as arguments  
      return make_thing(static_cast<long>(a), static_cast<long>(b));   
   }  
};  
  
```  
  
 適當時，預設編譯器行為可能不會報告錯誤 C2102。  在此範例中，如果在未指定 **\/Zc:rvalueCast** 時，採用身分轉型所建立之右值的位置，則編譯器不會報告錯誤：  
  
```cpp  
int main() {  
   int a = 1;  
   int *p = &a;   // Okay, take address of lvalue   
                  // Identity cast creates rvalue from lvalue;    
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value  
}  
```  
  
 如需 Visual C\+\+ 中一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  修改 \[其他選項\] 屬性，以包括 **\/Zc:rvalueCast**，然後選擇 \[確定\]。  
  
## 請參閱  
 [\/Zc \(一致性\)](../../build/reference/zc-conformance.md)