---
title: "編譯器警告 (層級 2) C4412 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4412"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4412"
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器警告 (層級 2) C4412
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 函式簽章含有型別 'type'，C\+\+ 物件在純程式碼與混合或機器碼之間傳遞並不安全。  
  
 編譯器偵測到可能會有潛在不安全的情況，可能會造成執行階段錯誤：正從 **\/clr:pure** 編譯呼叫經由 dllimport 匯入的函式，而且函式簽章中包含不安全的型別。  如果型別中包含為不安全型別或間接取值不安全型別的成員函式或資料成員，該型別就不安全。  
  
 這裡不安全的原因在於：純程式碼與機器碼 \(或是混合原生與 Managed\) 之間的預設呼叫慣例有差異。  \(經由 `dllimport`\) 將函式匯入 **\/clr:pure** 編譯時，請確定簽章中每一個型別的宣告都與匯出函式的編譯中的宣告完全相同 \(尤其要特別注意隱含呼叫慣例的差異\)。  
  
 虛擬成員函式尤其容易產生非預期的結果。但是即使非虛擬函式也應該加以測試，以確保您能夠取得正確結果。  如果您確定會取得正確結果，就可以忽略這項警告。  
  
 如需 **\/clr:pure** 的詳細資訊，請參閱 [如何：移轉至 \/clr:pure](../../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)。  
  
 C4412 預設為關閉。  如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 和 [dllexport、dllimport](../../cpp/dllexport-dllimport.md)。  
  
 若要解除這項警告，請從型別中移除所有函式。  
  
## 範例  
 下列範例會產生 C4412。  
  
```  
// C4412.cpp  
// compile with: /c /W2 /clr:pure  
#pragma warning (default : 4412)  
  
struct Unsafe {  
   virtual void __cdecl Test();  
};  
  
struct Safe {  
   int i;  
};  
  
__declspec(dllimport) Unsafe * __cdecl func();  
__declspec(dllimport) Safe * __cdecl func2();  
  
int main() {  
   Unsafe *pUnsafe = func();   // C4412  
   // pUnsafe->Test();  
  
   Safe *pSafe = func2();   // OK  
}  
```  
  
## 範例  
 下列範例是宣告兩種型別的標頭檔。  `Unsafe` 型別不安全是因為它有成員函式。  
  
```  
// C4412.h  
struct Unsafe {  
   // will be __clrcall if #included in pure compilation  
   // defaults to __cdecl in native or mixed mode compilation  
   virtual void Test(int * pi);  
  
   // try the following line instead  
   // virtual void __cdecl Test(int * pi);  
};  
  
struct Safe {  
   int i;  
};  
```  
  
## 範例  
 這個範例會以標頭檔中定義的型別匯出函式。  
  
```  
// C4412_2.cpp  
// compile with: /LD  
#include "C4412.h"  
  
void Unsafe::Test(int * pi) {  
   *pi++;  
}  
  
__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }  
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }  
```  
  
## 範例  
 **\/clr:pure** 編譯中的預設呼叫慣例與原生編譯不同。包含 C4412.h 時，`__clrcall` 將預設值為 `Test`。  如果您編譯並執行這個程式 \(不要使用 **\/c**\)，這個程式會擲回例外狀況。  
  
 下列範例會產生 C4412。  
  
```  
// C4412_3.cpp  
// compile with: /W2 /clr:pure /c /link C4412_2.lib  
#pragma warning (default : 4412)  
#include "C4412.h"  
  
__declspec(dllimport) Unsafe * __cdecl func();  
__declspec(dllimport) Safe * __cdecl func2();  
  
int main() {  
   int n = 7;  
   Unsafe *pUnsafe = func();   // C4412  
   pUnsafe->Test(&n);  
  
   Safe *pSafe = func2();   // OK  
}  
```