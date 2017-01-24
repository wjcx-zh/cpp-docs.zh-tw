---
title: "Double Thunking (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 編譯器選項 [C++], Double Thunking"
  - "Double Thunk"
  - "Interop [C++], Double Thunking"
  - "互通性 [C++], Double Thunking"
  - "混合的組件 [C++], Double Thunking"
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Double Thunking (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Double Thunking 是指，當 Managed 內容中的函式呼叫對 Visual C\+\+ Managed 函式進行呼叫，且程式執行為了要呼叫 Managed 函式而呼叫函式的原生進入點 \(Entry Point\) 時，您可能會遭遇到的效能問題。  本主題討論 Double Thunking 發生的地方及如何避免以改善效能。  
  
## 備註  
 根據預設，在使用 **\/clr** \(而非 **\/clr:pure**\) 進行編譯時，Managed 函式的定義會使編譯器產生 Managed 進入點和原生進入點。  如此，便可以從原生和 Managed 呼叫位置呼叫 Managed 函式。  不過，當原生進入點存在時，它便可能成為函式之所有呼叫的進入點。  如果呼叫函式是 Managed，則原生進入點會呼叫 Managed 進入點。  叫用函式時，實際上會用到兩個呼叫 \(因此，便發生 Double Thunking\)。  例如，虛擬函式一定是透過原生進入點來呼叫。  
  
 有一個解決方式，就是使用 [\_\_clrcall](../cpp/clrcall.md) 呼叫慣例 \(Calling Convention\) 通知編譯器不要產生 Managed 函式的原生進入點，如此，便只會從 Managed 內容呼叫函式。  
  
 同樣地，如果匯出 \([dllexport、dllimport](../cpp/dllexport-dllimport.md)\) Managed 函式，就會產生原生進入點，並且匯入及呼叫該函式的任何函式將會透過原生進入點進行呼叫。  若要避免這個情況中的 Double Thunking，請勿使用原生匯出\/匯入語意 \(Semantics\)；只要透過 `#using` \(請參閱 [\#using 指示詞](../preprocessor/hash-using-directive-cpp.md)\) 參考中繼資料即可。  
  
 編譯器已更新，以減少不必要的 Double Thunking。  例如，簽章 \(Signature\) 中具有 Managed 型別的任何函式 \(包含傳回型別\)，將會隱含地標記為 `__clrcall`。  如需 Double Thunk 排除的詳細資訊，請參閱 [http:\/\/msdn.microsoft.com\/msdnmag\/issues\/05\/01\/COptimizations\/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx)。  
  
## 範例  
  
### 說明  
 下列範例示範 Double Thunking。  當編譯機器碼時 \(不使用 **\/clr**\)，對 `main` 中虛擬函式的呼叫會產生一個 `T` 複製建構函式 \(Copy Constructor\) 的呼叫，以及一個解構函式 \(Destructor\) 的呼叫。  在使用 **\/clr** 和 `__clrcall` 宣告虛擬函式時，會完成類似的行為。  然而，只使用 **\/clr** 編譯時，函式呼叫會產生對複製建構函式的呼叫，但由於機器碼至 Managed 的 Thunk，所以會有另一個複製建構函式的呼叫。  
  
### 程式碼  
  
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
  
### 範例輸出  
  
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
  
## 範例  
  
### 說明  
 先前的範例示範了 Double Thunking 的存在，  這個範例會示範它的效用。  `for` 迴圈 \(Loop\) 會呼叫虛擬函式，而程式會報告執行時間。  使用 **\/clr** 編譯程式時，會報告最慢的時間，  而當不使用 **\/clr** 進行編譯，或虛擬函式是以 `__clrcall` 宣告時，就會報告最快的時間。  
  
### 程式碼  
  
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
  
### 範例輸出  
  
```  
4.2 seconds  
after calling struct S  
```  
  
## 請參閱  
 [混合 \(原生和 Managed\) 組件](../dotnet/mixed-native-and-managed-assemblies.md)