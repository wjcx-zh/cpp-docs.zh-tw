---
title: "Microsoft 對 C 和 C++ 的擴充功能 | Microsoft Docs"
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
  - "! 運算子, C++ 的擴充功能"
  - "!= 運算子"
  - "& 運算子, C/C++ 的擴充功能"
  - "&& 運算子"
  - "&= 運算子"
  - "^ 運算子, C/C++ 的擴充功能"
  - "^= 運算子, C++ 擴充功能"
  - "| 運算子, 擴充功能"
  - "|| 運算子"
  - "|= 運算子"
  - "~ 運算子, C/C++ 的擴充功能"
  - "And 運算子, C/C++ 的擴充功能"
  - "and_eq 運算子"
  - "compl 方法"
  - "擴充功能"
  - "擴充功能, C 語言"
  - "iso646.h 標頭"
  - "Microsoft 對 C/C++ 的擴充功能"
  - "NOT 運算子"
  - "not_eq 運算子"
  - "Or 運算子, Microsoft 對 C/C++ 的擴充功能"
  - "or_eq 運算子"
  - "Visual C, Microsoft 的擴充功能"
  - "Visual C++, C/C++ 的擴充功能"
  - "Xor 運算子, Microsoft 對 C/C++ 的擴充功能"
  - "xor_eq 運算子"
ms.assetid: e811a74a-45ba-4c00-b206-2f2321b8689a
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Microsoft 對 C 和 C++ 的擴充功能
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 擴充 ANSI C 或 ANSI C\+\+ 如以下標準。  
  
## 關鍵字  
 數個關鍵字加入。  在 [C\+\+ 關鍵字](../../cpp/keywords-cpp.md)的清單中，關鍵字中有兩個底線的是「 Visual C\+\+ 擴充功能」。  
  
## static const 整數 \(或列舉\) 成員的類別外定義  
 在標準 \(**\/Za**\) 之下，您必須對以下顯示的資料成員進行類別外定義。  
  
```  
class CMyClass  {  
   static const int max = 5;  
   int m_array[max];  
}  
...  
const int CMyClass::max;   // out of class definition  
```  
  
 在 **\/Ze** 之下，類別外定義對於靜態資料成員、const 整數資料成員和 const 列舉資料成員是選擇性的。  只有靜態和常數的積分和枚舉型別的整數和列舉可以在類別 \(Class\) 之內有初始設定式；這個初始設定運算式必須是常數運算式。  
  
 若要避免此錯誤，當類別外定義在標頭檔中提供，且標頭檔在多個原始程式檔中，請使用 [selectany](../../cpp/selectany.md)。  例如：  
  
```  
__declspec(selectany) const int CMyClass::max = 5;  
```  
  
## 轉型  
 C\+\+ 編譯器和 C 編譯器支援這類非 ANSI 轉換:  
  
-   非 ANSI 轉換產生左值 \(L\-Value\)：  例如：  
  
    ```  
    char *p;  
    (( int * ) p )++;  
    ```  
  
    > [!NOTE]
    >  此擴充功能可在只 C 語言取得。  您可以使用下列 ANSI C 標準格式在 C\+\+ 程式碼修改指標，就好像這是不同型別的指標。  
  
     前面的範例可以重新撰寫以符合 ANSI C 標準，如下所示：  
  
    ```  
    p = ( char * )(( int * )p + 1 );  
    ```  
  
-   非 ANSI 轉換函式指標成為資料指標：  例如：  
  
    ```  
    int ( * pfunc ) ();   
    int *pdata;  
    pdata = ( int * ) pfunc;  
    ```  
  
     若要執行同樣的轉換同時又維持 ANSI 相容性，您必須在將函式指標轉換為資料指標之前先將它轉換為 `uintptr_t`：  
  
    ```  
    pdata = ( int * ) (uintptr_t) pfunc;  
    ```  
  
## 可變長度引數清單  
 C\+\+和 C 這兩種編譯器都支援使用指定可變引數數目的函式宣告子 \(Declarator\)，後面接著一個提供型別的函式定義：  
  
```  
void myfunc( int x, ... );  
void myfunc( int x, char * c )  
{ }  
```  
  
## 單行註解  
 C 編譯器支援由雙正斜線 \(\/\/\) 字元引入的單行註解：  
  
```  
// This is a single-line comment.  
```  
  
## 範圍  
 C 編譯器支援下列範圍 \(Scope\) 相關功能。  
  
-   重新定義外部項目為 static：  
  
    ```  
    extern int clip();  
    static int clip()  
    {}  
    ```  
  
-   在同樣範圍內使用有利的 typedef 重新定義：  
  
    ```  
    typedef int INT;  
    typedef int INT;  
    ```  
  
-   函式宣告子具有檔案範圍：  
  
    ```  
    void func1()  
    {  
        extern int func2( double );  
    }  
    int main( void )  
    {  
        func2( 4 );    //  /Ze passes 4 as type double  
    }                  //  /Za passes 4 as type int  
    ```  
  
-   若要使用非常數運算式，初始化的區塊範圍變數的使用:  
  
    ```  
    int clip( int );  
    int bar( int );  
    int main( void )  
    {  
        int array[2] = { clip( 2 ), bar( 4 ) };  
    }  
    int clip( int x )  
    {  
        return x;  
    }  
    int bar( int x )  
    {  
        return x;  
    }  
    ```  
  
## 資料宣告和定義  
 C 編譯器支援下列資料宣告和定義功能。  
  
-   在一個初始設定式中混用字元與字串常數：  
  
    ```  
    char arr[5] = {'a', 'b', "cde"};  
    ```  
  
-   刪除 **unsigned int** 或 **signed int**以外，還有基底型別的位元欄位。  
  
-   沒有型別的宣告子:  
  
    ```  
    x;  
    int main( void )  
    {  
        x = 1;  
    }  
    ```  
  
-   可變大小陣列 \(Unsized Array\) 做為結構和等位的最後一個欄位：  
  
    ```  
    struct zero  
    {  
        char *c;  
        int zarray[];  
    };  
    ```  
  
-   未命名 \(匿名\) 的結構：  
  
    ```  
    struct  
    {  
        int i;  
        char *s;  
    };  
    ```  
  
-   未命名 \(匿名\) 的等位：  
  
    ```  
    union  
    {  
        int i;  
        float fl;  
    };  
    ```  
  
-   未命名的成員：  
  
    ```  
    struct s  
    {  
       unsigned int flag : 1;  
       unsigned int : 31;  
    }  
    ```  
  
## 內建浮點函式  
 C\+\+和 C 編譯器在被指定時，都支援內嵌產生 **x86 專屬資訊 \>\>** `atan、``atan2、``cos、``exp、``log、``log10、``sin、``sqrt 和` `tan 函式`  x86 專屬資訊結束**\/Oi**。  對於 C 編譯器，使用這些內建函式時將會失去 ANSI 一致性，因為它們不會設定 `errno` 變數。  
  
## 傳遞非常數指標參數給需要參考常數指標參數的函式  
 這是對 C\+\+ 的擴充功能。  這個程式碼會編譯 **\/Ze**:  
  
```  
typedef   int   T;  
  
const T  acT = 9;      // A constant of type 'T'  
const T* pcT = &acT;   // A pointer to a constant of type 'T'  
  
void func2 ( const T*& rpcT )   // A reference to a pointer to a constant of type 'T'  
{  
   rpcT = pcT;  
}  
  
T*   pT;               // A pointer to a 'T'  
  
void func ()  
{  
   func2 ( pT );      // Should be an error, but isn't detected  
   *pT   = 7;         // Invalidly overwrites the constant 'acT'  
}  
```  
  
## 未啟用 ISO646.H  
 在 **\/Ze** 之下，若要使用以下運算子的文字形式，必須包含 iso646.h：  
  
-   &&\(and\)  
  
-   &\=\(and\_eq\)  
  
-   &\(bitand\)  
  
-   &#124; \(bitor\)  
  
-   ~ \(compl\)  
  
-   \!\(not\)  
  
-   \!\= \(not\_eq\)  
  
-   &#124;&#124; \(or\)  
  
-   &#124;\= \(or\_eq\)  
  
-   ^ \(xor\)  
  
-   ^\= \(xor\_eq\)  
  
## 字串常值的位址型別為 const char \[\]，而非 const char \(\*\) \[\]  
 下列範例將在 **\/Za** 下輸出 char const \(\*\)\[4\]，但在 **\/Ze** 下會輸出 char const \[4\]。  
  
```  
#include <stdio.h>  
#include <typeinfo>  
  
int main()  
{  
    printf_s("%s\n", typeid(&"abc").name());  
}  
```  
  
## 請參閱  
 [\/Za、\/Ze \(停用語言擴充功能\)](../../build/reference/za-ze-disable-language-extensions.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)