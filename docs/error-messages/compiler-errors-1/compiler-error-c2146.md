---
title: "編譯器錯誤 C2146 | Microsoft Docs"
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
  - "C2146"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2146"
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2146
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

語法錯誤 : 遺漏 'token' \(在識別項 'identifier' 之前\)  
  
 編譯器必須要有 `token`，但卻找到 `identifier`。可能的原因：  
  
1.  拼字或大小寫錯誤。  
  
2.  識別項的宣告中遺漏型別規範。  
  
 這項錯誤可能是因為排印錯誤而造成。  錯誤 [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) 通常出現在此錯誤之前。  
  
## 範例  
 下列範例會產生 C2146。  
  
```  
// C2146.cpp  
class CDeclaredClass {};  
  
class CMyClass {  
   CUndeclared m_myClass;   // C2146  
   CDeclaredClass m_myClass2;   // OK  
};  
  
int main() {  
   int x;  
   int t x;   // C2146 : missing semicolon before 'x'  
}  
```  
  
## 範例  
 對 Visual Studio .NET 2003 的編譯器完成一致性處理後也可能會產生這種錯誤：遺漏 `typename` 關鍵字。  
  
 下列範例可在 Visual Studio .NET 2002 中編譯，但在 Visual Studio .NET 2003 中會失敗：  
  
```  
// C2146b.cpp  
// compile with: /c  
template <typename T>  
struct X {  
   struct Y {  
      int i;  
   };  
   Y memFunc();  
};  
  
template <typename T>  
X<T>::Y func() { }   // C2146  
  
// OK  
template <typename T>  
typename X<T>::Y func() { }  
```  
  
## 範例  
 對 Visual Studio .NET 2003 的編譯器完成符合標準處理後也會出現這個錯誤：明確特製化不再從主要樣板中尋找樣板參數。  
  
 明確特製化中不允許從主要樣板使用 `T`。  若要使程式碼在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中都有效，請以明確指定的型別，取代特製化中樣板參數的所有執行個體。  
  
 下列範例可在 Visual Studio .NET 中編譯，但在 Visual Studio .NET 2003 中會失敗：  
  
```  
// C2146_c.cpp  
// compile with: /c  
template <class T>   
struct S;  
  
template <>   
struct S<int> {  
   T m_t;   // C2146  
   int m_t2;   // OK  
};  
```