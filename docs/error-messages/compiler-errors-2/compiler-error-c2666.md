---
title: "編譯器錯誤 C2666 | Microsoft Docs"
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
  - "C2666"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2666"
ms.assetid: 78364d15-c6eb-439a-9088-e04a0176692b
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2666
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : number 多載具有類似的轉換  
  
 多載函式或運算子模稜兩可。型式參數清單 \(Formal Parameter List\) 可能太類似，以致編譯器無法解決語意模糊。若要解決這項錯誤，請明確轉換實質參數的其中一個或多個。  
  
 下列範例會產生 C2666：  
  
```  
// C2666.cpp  
struct complex {  
   complex(double);  
};  
  
void h(int,complex);  
void h(double, double);  
  
int main() {  
   h(3,4);   // C2666  
}  
```  
  
 對 Visual Studio .NET 2003 的編譯器完成一致性處理後也可能會產生這項錯誤：  
  
-   二進位運算子和使用者定義的指標型別轉換  
  
-   限定性條件轉換與自身轉換不同  
  
 以二元運算子 \<、\>、\<\= 和 \>\= 而言，如果參數型別定義使用者定義的轉換運算子，以轉換成運算元的型別，則現在傳遞的參數會隱含地轉換成該運算元的型別。  現在可能會產生模稜兩可 \(Ambiguity\) 的情況。  
  
 若要使程式碼在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中都有效，請使用函式語法明確呼叫類別運算子。  
  
## 範例  
  
```  
// C2666b.cpp  
#include <string.h>  
#include <stdio.h>  
  
struct T   
{  
    T( const T& copy )   
    {  
        m_str = copy.m_str;  
    }  
  
    T( const char* str )   
    {  
        int iSize = (strlen( str )+ 1);  
        m_str = new char[ iSize ];  
        if (m_str)  
            strcpy_s( m_str, iSize, str );  
    }  
  
    bool operator<( const T& RHS )   
    {  
        return m_str < RHS.m_str;  
    }  
  
    operator char*() const   
    {  
        return m_str;  
    }  
  
    char* m_str;  
};  
  
int main()   
{  
    T str1( "ABCD" );  
    const char* str2 = "DEFG";  
  
    // Error – Ambiguous call to operator<()  
    // Trying to convert str1 to char* and then call   
    // operator<( const char*, const char* )?  
    //  OR  
    // trying to convert str2 to T and then call  
    // T::operator<( const T& )?  
  
    if( str1 < str2 )   // C2666  
  
    if ( str1.operator < ( str2 ) )   // Treat str2 as type T  
        printf_s("str1.operator < ( str2 )\n");  
  
    if ( str1.operator char*() < str2 )   // Treat str1 as type char*  
        printf_s("str1.operator char*() < str2\n");  
}  
```  
  
## 範例  
 下列範例會產生 C2666  
  
```  
// C2666c.cpp  
// compile with: /c  
  
enum E   
{  
    E_A,   E_B  
};  
  
class A   
{  
    int h(const E e) const {return 0; }  
    int h(const int i) { return 1; }  
    // Uncomment the following line to resolve.  
    // int h(const E e) { return 0; }  
  
    void Test()   
    {  
        h(E_A);   // C2666  
        h((const int) E_A);  
        h((int) E_A);  
    }  
};  
```