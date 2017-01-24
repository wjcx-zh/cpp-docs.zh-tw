---
title: "literal (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "literal"
  - "literal_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "literal keyword [C++]"
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# literal (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

變數 \(資料成員\) 標記為 **\/clr** 編輯的 `literal` 是 `static const` 變數的原生對等用法。  
  
## 所有平台  
 **備註**  
  
 \(這個語言功能沒有適用於所有執行階段的備註\)。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **備註**  
  
 \(這個語言功能沒有只適用於 Windows 執行階段的備註。\)  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## Common Language Runtime  
  
## 備註  
 當宣告和值都必須是一個常數整數、enum 或字串型別，則標記為 `literal`的資料成員必須初始化。  從初始化運算式的型別轉換為靜態常數資料成員的型別不能需要使用者定義的轉換。  
  
 記憶體不為執行階段的常值欄位配置; 編譯器在類別的中繼資料插入值。  
  
 變數標示 `static const` 不會有中繼資料給其他編譯器。  
  
 如需詳細資訊，請參閱[Static](../misc/static-cpp.md)與[const](../cpp/const-cpp.md)。  
  
 `literal` 是內容相關性關鍵字。  如需詳細資訊，請參閱[視內容而有所區別的關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
## 範例  
 這個範例會顯示 `literal` 變數表示 `static`。  
  
```  
// mcppv2_literal.cpp  
// compile with: /clr  
ref struct X {  
   literal int i = 4;  
};  
  
int main() {  
   int value = X::i;  
}  
```  
  
## 範例  
 下列範例在中繼資料中顯示文字的影響:  
  
```  
// mcppv2_literal2.cpp  
// compile with: /clr /LD  
public ref struct A {  
   literal int lit = 0;  
   static const int sc = 1;  
};  
```  
  
 請注意在中繼資料中的差異 `sc` 和 `lit`的: `modopt` 指示詞套用至 `sc`，這表示它可以由其他編譯器忽略。  
  
```  
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)  
```  
  
```  
.field public static literal int32 lit = int32(0x0000000A)  
```  
  
## 範例  
 下列範例中，會建立在 C\# 中，參考在先前範例中建立的中繼資料並顯示 `literal` 和 `static const` 變數的影響:  
  
```  
// mcppv2_literal3.cs  
// compile with: /reference:mcppv2_literal2.dll  
// A C# program  
class B {  
   public static void Main() {  
      // OK  
      System.Console.WriteLine(A.lit);  
      System.Console.WriteLine(A.sc);  
  
      // C# does not enforce C++ const  
      A.sc = 9;  
      System.Console.WriteLine(A.sc);  
  
      // C# enforces const for a literal  
      A.lit = 9;   // CS0131  
  
      // you can assign a C++ literal variable to a C# const variable  
      const int i = A.lit;  
      System.Console.WriteLine(i);  
  
      // but you cannot assign a C++ static const variable  
      // to a C# const variable  
      const int j = A.sc;   // CS0133  
      System.Console.WriteLine(j);  
   }  
}  
```  
  
## 需求  
 編譯器選項：**\/clr**  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)