---
title: "編譯器錯誤 C2146 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2146
dev_langs:
- C++
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 92e94ae29c1a7a3fc6adfdc0b3e82f5ce4dfcaf0
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2146"></a>編譯器錯誤 C2146
語法錯誤： 遺漏 'token' 之前識別項 'identifier'  
  
 編譯器預期`token`找到`identifier`改為。  可能的原因：  
  
1.  拼字或大小寫錯誤。  
  
2.  識別項的宣告中遺漏類型規範。  
  
 這個錯誤可能被因拼字錯誤。 錯誤[C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md)通常前面出現此錯誤。  
  
## <a name="example"></a>範例  
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
  
## <a name="example"></a>範例  
 也可以針對 Visual Studio.NET 2003年所進行的編譯器一致性工作產生這個錯誤： 遺漏`typename`關鍵字。  
  
 下列範例會在 Visual Studio.NET 2002年中編譯，但 Visual Studio.NET 2003年中將會失敗：  
  
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
  
## <a name="example"></a>範例  
 您也會看到這個錯誤，因為針對 Visual Studio.NET 2003年所進行的編譯器一致性處理而： 明確特製化不會再尋找主要樣板的樣板參數。  
  
 使用`T`從主要範本中不允許明確特製化。 針對 Visual c + + 的 Visual Studio.NET 2003年和 Visual Studio.NET 版本中都有效的程式碼，取代明確特製化的型別在特製化的範本參數的所有執行個體。  
  
 下列範例會在 Visual Studio.NET 中編譯，但 Visual Studio.NET 2003年中將會失敗：  
  
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
