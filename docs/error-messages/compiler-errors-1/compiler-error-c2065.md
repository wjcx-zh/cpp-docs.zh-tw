---
title: "編譯器錯誤 C2065 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2065"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2065"
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2065
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier'：未宣告的識別項  
  
 必須先在宣告中指定變數的類型，才可加以使用。  必須先在宣告或原型中指定函式使用的參數，才可使用此函式。  
  
 可能的原因：  
  
1.  識別項名稱拼錯了。  
  
2.  識別項使用錯誤的大寫和小寫字母。  
  
3.  遺漏字串常數之後的右引號。  
  
4.  您正在使用 C 執行階段的偵錯版本進行編譯、在 `for` 迴圈中宣告 Standard C\+\+ 程式庫 Iterator 變數，然後嘗試在 `for` 迴圈範圍外使用該 Iterator 變數。  使用 C 執行階段的偵錯版本編譯 C\+\+ Standard 程式庫程式碼表示 [\/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)。  如需詳細資訊，請參閱[偵錯迭代器支援](../../standard-library/debug-iterator-support.md)。  
  
5.  您可能會在您的建置環境中目前不支援的 SDK 標頭檔中呼叫函式。  
  
6.  省略所需的 Include 檔案，特別是當您定義 `VC_EXTRALEAN`、`WIN32_LEAN_AND_MEAN`或 `WIN32_EXTRA_LEAN` 時。  這些符號會從 windows.h 和 afxv\_w32.h 中排除某些標頭檔，以加速編譯。  \(在 windows.h 和 afxv\_w32.h 中尋找所排除項目的最新描述\)。  
  
7.  不當的命名空間範圍。  例如，若要解析不完整的 C\+\+ Standard 程式庫函式和運算子，您必須透過 `using` 指示詞指定 `std` 命名空間。  下列範例無法編譯，因為 `using` 指示詞已註解排除，而 `cout` 已定義於 `std` 命名空間：  
  
## 範例  
 下列範例會產生 C2065，並示範如何修正此問題。  
  
```  
// C2065.cpp  
// compile with: /EHsc  
// using namespace std;   // Uncomment this line to fix  
#include <iostream>  
int main() {  
   cout << "Hello" << endl;   // C2065  
  
   // Or try the following line instead  
   std::cout << "Hello" << std::endl;  
}  
```  
  
## 範例  
 呼叫泛型函式時，如果無法從使用的參數推論預定的類型引數，則編譯器會回報錯誤。  如需詳細資訊，請參閱[Generic Functions \(C\+\+\/CLI\)](../../windows/generic-functions-cpp-cli.md)。  
  
 下列範例會產生 C2065，並示範如何修正此問題。  
  
```  
// C2065_b.cpp  
// compile with: /clr  
generic <typename ItemType>  
void G(int i) {}  
  
int main() {  
   // global generic function call  
   G<T>(10);   // C2065  
   G<int>(10);   // OK - fix with a specific type argument  
}  
```  
  
## 範例  
 針對 Visual C\+\+ 2005 所進行的編譯器一致性工作，也可能會導致這個錯誤：Visual C\+\+ 屬性的參數檢查。  
  
 下列範例會產生 C2065，並示範如何修正此問題。  
  
```  
// C2065_c.cpp  
// compile with: /c  
[module(DLL, name=MyLibrary)];   // C2065  
// try the following line instead  
// [module(dll, name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```