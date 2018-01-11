---
title: "Double Thunk （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1d905f962af6a9cf07ecb0926503fc24e21c0136
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="double-thunking-c"></a>Double Thunking (C++)
Double thunking 指的是效能的 Visual c + + managed 函式，以及在程式執行的受管理的內容呼叫的函式呼叫才能呼叫 managed 函式呼叫函式的原生進入點時，您可能遇到損失。 本主題討論 double thunking 的發生位置，以及避免可改善效能。  
  
## <a name="remarks"></a>備註  
 根據預設，當編譯**/clr**，managed 函式的定義會導致編譯器產生的 managed 的進入點和原生進入點。 這可讓 managed 函式呼叫從原生和 managed 呼叫站台。 不過，原生進入點存在時，它可以是函式的所有呼叫的進入點。 如果呼叫的函式為 managed，原生進入點然後會呼叫 managed 的進入點。 作用中，兩個呼叫，才能叫用函式 (因此，double thunking)。 例如，透過原生進入點一律呼叫虛擬函式。  
  
 一個解決方法是，告知編譯器不要產生 managed 函式的原生進入點，此函式只會呼叫從受管理的內容中，使用[__clrcall](../cpp/clrcall.md)呼叫慣例。  
  
 同樣地，如果您匯出 ([dllexport、 dllimport](../cpp/dllexport-dllimport.md)) managed 函式，會產生原生進入點和任何函式，匯入，然後呼叫該函式會呼叫透過原生進入點。 若要避免 double thunking 在此情況下，不使用原生的匯出/匯入語意。只參考的中繼資料透過`#using`(請參閱[#using 指示詞](../preprocessor/hash-using-directive-cpp.md))。  
  
 若要減少不必要的 double thunking 編譯器已更新。 例如，managed 型別 （包括傳回型別） 的簽章中具有的任何函式會隱含地被標示為`__clrcall`。 多個雙 thunk 刪除的詳細資訊，請參閱[http://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx)。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會示範 double thunking。 原生編譯時 (不含**/clr**) 中的虛擬函式呼叫`main`會產生一個呼叫`T`的複製建構函式和解構函式呼叫。 虛擬函式宣告用達成類似的行為**/clr**和`__clrcall`。 不過，只要編譯時**/clr**、 函式呼叫會產生複製建構函式呼叫，但沒有另一個呼叫複製建構函式，因為原生 managed 的 thunk。  
  
### <a name="code"></a>程式碼  
  
```  
// double_thunking.cpp  
// compile with: /clr  
#include <stdio.h>  
struct T {  
   T() {  
      puts(__FUNCSIG__);  
   }  
  
   T(const T&) {  
      puts(__FUNCSIG__);  
   }  
  
   ~T() {  
      puts(__FUNCSIG__);  
   }  
  
   T& operator=(const T&) {  
      puts(__FUNCSIG__);  
      return *this;  
   }  
};  
  
struct S {  
   virtual void /* __clrcall */ f(T t) {};  
} s;  
  
int main() {  
   S* pS = &s;  
   T t;  
  
   printf("calling struct S\n");  
   pS->f(t);  
   printf("after calling struct S\n");  
}  
```  
  
### <a name="sample-output"></a>範例輸出  
  
```  
__thiscall T::T(void)  
calling struct S  
__thiscall T::T(const struct T &)  
__thiscall T::T(const struct T &)  
__thiscall T::~T(void)  
__thiscall T::~T(void)  
after calling struct S  
__thiscall T::~T(void)  
```  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 前一個範例所示範 double thunking 的存在。 這個範例會示範其效果。 `for`迴圈就會呼叫虛擬函式和程式報告執行時間。 最慢的時間與編譯程式時回報**/clr**。 而不編譯時，會報告最快時間**/clr**或如果虛擬函式以宣告`__clrcall`。  
  
### <a name="code"></a>程式碼  
  
```  
// double_thunking_2.cpp  
// compile with: /clr  
#include <time.h>  
#include <stdio.h>   
  
#pragma unmanaged  
struct T {  
   T() {}  
   T(const T&) {}  
   ~T() {}  
   T& operator=(const T&) { return *this; }  
};  
  
struct S {  
   virtual void /* __clrcall */ f(T t) {};  
} s;  
  
int main() {  
   S* pS = &s;  
   T t;  
   clock_t start, finish;  
   double  duration;  
   start = clock();  
  
   for ( int i = 0 ; i < 1000000 ; i++ )  
      pS->f(t);  
  
   finish = clock();  
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);  
   printf( "%2.1f seconds\n", duration );  
   printf("after calling struct S\n");  
}  
```  
  
### <a name="sample-output"></a>範例輸出  
  
```  
4.2 seconds  
after calling struct S  
```  
  
## <a name="see-also"></a>請參閱  
 [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)