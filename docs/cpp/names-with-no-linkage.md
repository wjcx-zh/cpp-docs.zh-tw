---
title: "沒有連結的名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "列舉程式 [C++], 連結"
  - "函式參數 [C++]"
  - "函式 [C++], 參數"
  - "名稱 [C++], 沒有連結"
  - "typedef 名稱, 連結"
ms.assetid: 7174c500-12d2-4572-8c16-63c27c758fb1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 沒有連結的名稱
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

唯一沒有連結的名稱為：  
  
-   函式參數。  
  
-   未宣告為 `extern` 或 **static** 的區塊範圍名稱。  
  
-   列舉程式。  
  
-   在 `typedef` 陳述式中宣告的名稱。  當 `typedef` 陳述式是用來為未命名的類別類型提供名稱時例外。  如果類別具有外部連結，其名稱可能也會有外部連結。  下列範例顯示 `typedef` 名稱有外部連結的情況：  
  
    ```  
    // names_with_no_linkage.cpp  
    typedef struct  
    {  
       short x;  
       short y;  
    } POINT;  
  
    extern int MoveTo( POINT pt );  
  
    int main()  
    {  
    }  
    ```  
  
     `typedef` 名稱 `POINT` 會成為未命名結構的類別名稱。  接著會使用它來宣告具有外部連結的函式。  
  
 由於 `typedef` 名稱沒有連結，其在轉譯單位之間可能會有不同的定義。  由於是分開進行編譯，所以編譯器無法偵測這些差異。  因此，這類錯誤直到連結時才會偵測到。  請考慮下列情況：  
  
```  
// Translation unit 1  
typedef int INT  
  
INT myInt;  
...  
  
// Translation unit 2  
typedef short INT  
  
extern INT myInt;  
...  
```  
  
 上述程式碼在連結時會產生「未解析的外部」錯誤。  
  
## 範例  
 C\+\+ 函式只能在檔案或類別範圍內進行定義。  下列範例說明如何定義函式並顯示一個錯誤的函式定義：  
  
```  
// function_definitions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
void ShowChar( char ch );    // Declare function ShowChar.  
  
void ShowChar( char ch )     // Define function ShowChar.  
{                            // Function has file scope.  
   cout << ch;  
}  
  
struct Char                  // Define class Char.  
{  
    char Show();             // Declare Show function.  
    char Get();              // Declare Get function.  
    char ch;  
};  
  
char Char::Show()            // Define Show function  
{                            //  with class scope.  
    cout << ch;  
    return ch;  
}  
  
void GoodFuncDef( char ch )  // Define GoodFuncDef  
{                            //  with file scope.  
    int BadFuncDef( int i )  // C2601, Erroneous attempt to  
    {                        //  nest functions.  
        return i * 7;  
    }  
    for( int i = 0; i < BadFuncDef( 2 ); ++i )  
        cout << ch;  
    cout << "\n";  
}  
```  
  
## 請參閱  
 [程式和連結](../cpp/program-and-linkage-cpp.md)