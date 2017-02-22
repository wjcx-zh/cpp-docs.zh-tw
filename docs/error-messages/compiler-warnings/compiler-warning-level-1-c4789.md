---
title: "編譯器警告 (層級 1) C4789 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4789"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4789"
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# 編譯器警告 (層級 1) C4789
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

大小 N 位元組的緩衝區 'identifier' 會溢位；將從位移 L 開始寫入 M 位元組  
  
 使用特定的 C 執行階段 \(CRT\) 函式、參數傳遞，及執行指派時，如此在編譯時期會知道資料大小時，會警告緩衝區溢位。  這項警告是針對可能逃避一般的資料大小不符偵測的情況。  
  
 複製資料 \(其長度在編譯時間已知\)，並置於編譯時期已知其大小的資料區塊時，如果區塊太小無法容納資料，則會出現警告。  必須使用下列其中一個 CRT 函式的內建形式來完成複製：  
  
-   [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)  
  
-   [memset](../../c-runtime-library/reference/memset-wmemset.md)  
  
-   [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)、[wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)  
  
 使用轉型，然後嘗試從 lvalue 參考複製指派時，如果參數資料類型不符，也會出現警告。  
  
 Visual C\+\+ 可能會為永遠不會執行的程式碼路徑產生這個警告。  您可以使用 `#pragma` \(如這個範例所示\) 以暫時停用警告：  
  
 `#pragma(push)`  
  
 `#pragma warning ( disable : 4789 )`  
  
 `// unused code that generates compiler warning C4789`  
  
 `#pragma(pop)`  
  
 這可避免 Visual C\+\+ 產生該特定程式碼區塊的警告。  `#pragma(push)` 會先保留現有的狀態，直到 `#pragma warning(disable: 4789)` 變更它。  `#pragma(pop)` 還原推入的狀態，並移除 `#pragma warning(disable:4789)` 的效果。  如需 C\+\+ 前置處理器指示詞 `#pragma` 的詳細資訊 ，請參閱[warning](../../preprocessor/warning.md)和 [Pragma 指示詞和 \_\_Pragma 關鍵字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。  
  
## 範例  
 下列範例會產生 C4789。  
  
```  
// C4789.cpp  
// compile with: /Oi /W1 /c  
#include <string.h>  
#include <stdio.h>  
  
int main()   
{  
    char a[20];  
    strcpy(a, "0000000000000000000000000\n");   // C4789  
  
    char buf2[20];  
    memset(buf2, 'a', 21);   // C4789  
  
    char c;  
    wchar_t w = 0;  
    memcpy(&c, &w, sizeof(wchar_t));  
}  
```  
  
## 範例  
 下列範例也會產生 C4789。  
  
```  
// C4789b.cpp  
// compile with: /W1 /O2 /c  
// processor: x86  
short G;  
  
void main()  
{  
   int * p = (int *)&G;   
   *p = 3;   // C4789 - writes an int through a pointer to short  
}   
```