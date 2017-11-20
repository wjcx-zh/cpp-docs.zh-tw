---
title: "編譯器錯誤 C2666 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2666
dev_langs: C++
helpviewer_keywords: C2666
ms.assetid: 78364d15-c6eb-439a-9088-e04a0176692b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fb6c45ad153a428d090d05c8fa24c05eef024607
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2666"></a>編譯器錯誤 C2666
'identifier': 數字的多載具有類似的轉換  
  
 多載函式或運算子模稜兩可。   型式參數清單可能太類似編譯器無法解析模稜兩可。  若要解決這個錯誤，明確轉換一或多個實際的參數。  
  
 下列範例會產生 C2666:  
  
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
  
 這項錯誤也會導致針對 Visual Studio.NET 2003年所進行的編譯器一致性工作：  
  
-   二元運算子，以及使用者定義的指標類型轉換  
  
-   限定性條件轉換不是身分識別轉換相同  
  
 以二元運算子\<，>， \<= 和 > =、 傳遞參數現在就隱含地轉換成運算元的類型如果參數的型別定義使用者定義轉換運算子，將轉換成運算元的類型。 沒有現在可能模稜兩可。  
  
 針對 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中有效的程式碼，呼叫類別運算子，明確地使用函式語法。  
  
## <a name="example"></a>範例  
  
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
  
    // Error - Ambiguous call to operator<()  
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
  
## <a name="example"></a>範例  
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