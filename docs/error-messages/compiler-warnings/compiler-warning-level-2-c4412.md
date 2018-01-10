---
title: "編譯器警告 （層級 2） C4412 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4412
dev_langs: C++
helpviewer_keywords: C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92898b9c8e8845ecc8bc650b80cf41a33b3a59d9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-2-c4412"></a>編譯器警告 (層級 2) C4412
'function': 函式簽章含有類型 'type';C + + 物件是純程式碼之間傳遞的不安全與混合或原生。  
  
 **/Clr: pure** Visual Studio 2015 中的編譯器選項已被取代。  
  
 編譯器偵測到可能不安全的情況，可能會導致執行階段錯誤： 從進行呼叫**/clr: pure**編譯模組匯入透過 dllimport 和函式簽章的函式包含不安全的類型. 如果它包含的成員函式，或具有不安全的類型或不安全的類型間接取值的資料成員，則不安全的類型。  
  
 這是不安全，因為在預設的呼叫慣例純粹的和原生程式碼之間的差異 （或混合的原生和 managed）。 當匯入 (透過`dllimport`) 函式匯入**/clr: pure**編譯時，請確定簽章中的每個型別的宣告都與匯出函式 （尤其要特別注意的編譯差異隱含呼叫慣例）。  
  
 虛擬成員函式是特別容易產生非預期的結果。  不過，即使非虛擬函式應該測試，以確保您能取得正確的結果。 如果您不確定您要取得正確的結果，您可以忽略此警告。  
  
 如需詳細資訊**/clr: pure**，請參閱[How to： 移轉至 /clr: pure (C + + CLI)](../../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)。  
  
 C4412 預設為關閉。 請參閱[編譯器警告為關閉的預設](../../preprocessor/compiler-warnings-that-are-off-by-default.md)和[dllexport、 dllimport](../../cpp/dllexport-dllimport.md)如需詳細資訊。  
  
 若要解決這個警告，移除型別中的所有函式。  
  
## <a name="example"></a>範例  
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
  
## <a name="example"></a>範例  
 下列範例會宣告兩種類型的標頭檔。 `Unsafe`類型是不安全，因為它有成員函式。  
  
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
  
## <a name="example"></a>範例  
 這個範例會匯出函式標頭檔中定義的型別。  
  
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
  
## <a name="example"></a>範例  
 預設呼叫慣例**/clr: pure**編譯為原生編譯而不同。  當 C4412.h 隨附`Test`預設為`__clrcall`。 如果您編譯並執行此程式 (請勿使用**/c**)，程式將會擲回例外狀況。  
  
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