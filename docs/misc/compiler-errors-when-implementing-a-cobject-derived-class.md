---
title: "實作 CObject 衍生類別時發生編譯器錯誤 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "編譯原始程式碼, CObject 衍生類別"
  - "錯誤 [C++]"
  - "錯誤 [C++], 編譯器"
  - "CObject 類別, 衍生類別的編譯器錯誤"
ms.assetid: 9f249b52-aeff-41a1-8a74-a52aa08c4fcf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# 實作 CObject 衍生類別時發生編譯器錯誤
如果您實作衍生自 `CObject` 的類別，並且所撰寫的程式碼呼叫類別之複製建構函式或指派運算子，則編譯器可能會報告與下面類似的錯誤：  
  
```  
error C2660: 'CSample::CSample' : function does not take 1 parameters error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 編譯下面 \[範例程式碼\] 區段中的範例，就可以重現問題。  
  
> [!NOTE]
>  本文中所示的範例程式碼會產生下列錯誤訊息：  
  
```  
error C2558: 'CSample::CSample' : no copy constructor available error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 編譯器錯誤的原因是 `CObject` 在 AFX.h 檔案中宣告私用複製建構函式和指派運算子。 因此，編譯器不會產生 `CObject` 衍生類別的預設複製建構函式和指派運算子。 因為編譯器找不到類別中所宣告的這些函式，所以它會報告錯誤。  
  
 若要避免編譯器錯誤，您需要實作 `CObject` 衍生類別的複製建構函式和指派運算子。 下面的範例程式碼說明這個錯誤。 您可以取消註解範例程式碼中所指出的行，以避免錯誤。  
  
## 程式碼範例  
  
```  
// _error_Compiler_Errors_when_Implementing_a_CObject.2d.Derived_Class.cpp /* Compile options needed: /c */ // replace with #define _CONSOLE when compiling for Windows NT #define _DOS #include <afx.h> class CSample : public CObject { private: short m_nValue; public: // uncomment the lines below to avoid the compiler errors //    CSample() {} //    CSample( const CSample &s )  // copy ctor //        { m_nValue = s.m_nValue; } //    CSample& operator=( const CSample &s )  // assignment operator //        { m_nValue = s.m_nValue; return *this; } }; int main() { CSample a; CSample b = a; a = b; }  
  
```  
  
## 請參閱  
 [編譯器警告s C4600 Through C4999](../error-messages/compiler-warnings/compiler-warnings-c4600-through-c4799.md)