---
title: "範例程式 | Microsoft Docs"
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
  - "C"
ms.assetid: fc22ef82-9caa-425f-b201-2891bc123d1f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 範例程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列 C 原始程式包含兩個原始程式檔。  它提供 C 程式中各種宣告和定義的概觀。  本書的其餘章節說明如何撰寫這些宣告、定義和初始化，以及如何使用 **static** 和 `extern` 之類的 C 關鍵字。  `printf` 函式會在 C 標頭檔 STDIO.H 中宣告。  
  
 `main` 和 `max` 函式假設在不同的檔案中，程式執行會從 `main` 函式開始。  沒有任何明確的使用者函式會在 `main` 之前執行。  
  
```  
/*****************************************************************  
                    FILE1.C - main function  
*****************************************************************/  
  
#define ONE     1  
#define TWO     2  
#define THREE   3  
#include <stdio.h>  
  
int a = 1;                       // Defining declarations      
int b = 2;                       //  of external variables      
  
extern int max( int a, int b );  // Function prototype          
  
int main()                       // Function definition         
{                                //  for main function          
    int c;                       // Definitions for      
    int d;                       //  two uninitialized  
                                 //  local variables  
  
    extern int u;                // Referencing declaration     
                                 //  of external variable       
                                 //  defined elsewhere          
    static int v;                // Definition of variable      
                                 //  with continuous lifetime   
  
    int w = ONE, x = TWO, y = THREE;  
    int z = 0;  
  
    z = max( x, y );             // Executable statements      
    w = max( z, w );  
    printf_s( "%d %d\n", z, w );  
    return 0;  
}  
  
/****************************************************************  
            FILE2.C - definition of max function  
****************************************************************/  
  
int max( int a, int b )          // Note formal parameters are     
                                 //  included in function header   
{  
    if( a > b )  
        return( a );  
    else  
        return( b );  
}  
```  
  
 FILE1.C 包含 `max` 函式的原型。  這類宣告有時稱為「向前宣告」，因為會在使用之前宣告。  `main` 函式的定義包括對 `max` 的呼叫。  
  
 以 `#define` 開頭的行是前置處理器指示詞。  這些指示詞會指示前置處理器將 FILE1.C 中的 `ONE`、`TWO` 和 `THREE` 分別取代為 `1`、`2` 和 `3` 等識別項。  不過，指示詞不適用於 FILE2.C，後者會單獨編譯，然後與 FILE1.C 連結。  以 `#include` 開頭的行會指示編譯器包含 STDIO.H 檔案，該檔案包含 `printf` 函式的原型。  《前置處理器參考》中會說明[前置處理器指示詞](../preprocessor/preprocessor-directives.md)。  
  
 FILE1.C 會使用定義宣告來初始化全域變數 `a` 和 `b`。  會宣告區域變數 `c` 和 `d`，但不會初始化。  都會為這些變數配置儲存區。  靜態和外部變數 `u` 和 `v` 會自動初始化為 0。  因此，宣告時只有 `a`、`b`、`u` 和 `v` 包含有意義的值，因為它們會明確或隱含地初始化。  FILE2.C 包含 `max`的函式定義。  這個定義符合 FILE1.C 中對 `max` 的呼叫。  
  
 [存留期、範圍、可視性和連結](../c-language/lifetime-scope-visibility-and-linkage.md)中會討論識別項的存留期和可視性。  如需函式的詳細資訊，請參閱[函式](../c-language/functions-c.md)。  
  
## 請參閱  
 [原始程式檔和來源程式](../c-language/source-files-and-source-programs.md)