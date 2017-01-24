---
title: "編譯器警告 (層級 1) C4350 | Microsoft Docs"
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
  - "C4350"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4350"
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4350
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

行為變更: 呼叫了 'member1' 而不是 'member2'  
  
 值無法繫結至非常數參考。  在舊版 Visual C\+\+ 中，可以在直接初始化中，將變數繫結至非常數參考。  這程式碼現在會發出警告。  
  
 為達到回溯相容性 \(Backward Compatibility\)，仍然可以將右值繫結至非常數參考，但盡可能取標準轉換。  
  
 這項警告表示從 Visual C\+\+ .NET 2002 編譯器以來的行為變更。  如果啟用，可能會對正確程式碼發出這項警告。  例如，使用 **std::auto\_ptr** 類別樣板時，可能就會發出這項警告。  
  
 如果接到這項警告，請檢查您的程式碼，查看是否依繫結右值至非常數參考而產生。  加入 const 至參考，或另外提供常數參考多載，也許就能解決問題。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列範例會產生 C4350：  
  
```  
// C4350.cpp  
// compile with: /W1  
#pragma warning (default : 4350)  
class A {};  
  
class B  
{  
public:  
   B(B&){}  
   // try the following instead  
   // B(const B&){}  
  
   B(A){}  
   operator A(){ return A();}  
};  
  
B source() { return A(); }  
  
int main()  
{  
   B ap(source());   // C4350  
}  
```