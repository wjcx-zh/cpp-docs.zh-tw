---
title: "CRT 初始化 | Microsoft Docs"
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
  - "CRT 初始化 [C++]"
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# CRT 初始化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題說明 CRT 如何以機器碼初始化全域狀態。  
  
 根據預設，連結器包含 CRT 程式庫，這提供它自己的啟始程式碼。  這個啟始程式碼初始化 CRT 程式庫，呼叫全域初始設定式，然後呼叫使用者提供的 `main` 函式至主控台應用程式。  
  
## 初始化全域物件  
 請考慮下列程式碼：  
  
```  
int func(void)  
{  
    return 3;  
}  
  
int gi = func();  
  
int main()  
{  
    return gi;  
}  
```  
  
 根據 C\/C\+\+ 準則，`func()` ，在 `main()` 執行之前，必須先行呼叫。  但是誰呼叫它?  
  
 一種判斷方法是在 `func()`上設定中斷點，偵錯應用程式並檢查堆疊。  因為 CRT 原始程式碼隨附於 Visual Studio，這是可能的。  
  
 當您瀏覽堆疊上的函式，您會找到 CRT 於函式清單指標迴圈執行，並在遇到它們時執行。  這些函式不是類似於 `func()` 就是建構函式的類別執行個體。  
  
 CRT 從 Visual C\+\+ 編譯器取得函式指標清單。  當編譯器查看全域初始設定式時，它會在 `.CRT$XCU` 區段中生成動態初始設定式 \(其中 `CRT` 是區段名稱，而 `XCU` 是群組名稱\)。  若要取得那些動態初始設定式清單，執行 **dumpbin \/all main.obj** 命令，然後搜尋 `.CRT$XCU` 區段 \(當 main.cpp 編譯為 C \+\+. 檔案，而不是 C 檔案\) 。  它會類似下列所示:  
  
```  
SECTION HEADER #6  
.CRT$XCU name  
       0 physical address  
       0 virtual address  
       4 size of raw data  
     1F2 file pointer to raw data (000001F2 to 000001F5)  
     1F6 file pointer to relocation table  
       0 file pointer to line numbers  
       1 number of relocations  
       0 number of line numbers  
40300040 flags  
         Initialized Data  
         4 byte align  
         Read Only  
  
RAW DATA #6  
  00000000: 00 00 00 00                                      ....  
  
RELOCATIONS #6  
                                                Symbol    Symbol  
 Offset    Type              Applied To         Index     Name  
 --------  ----------------  -----------------  --------  ------  
 00000000  DIR32                      00000000         C  ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))  
```  
  
 CRT 定義兩個指標:  
  
-   `.CRT$XCA` \(英文\) 中的`__xc_a` \(英文\)  
  
-   `.CRT$XCZ` \(英文\) 中的`__xc_z` \(英文\)  
  
 兩個群組都沒有任何其他符號定義，除了 `__xc_a` 和 `__xc_z`。  
  
 現在，當連結器讀取各種 `.CRT` 群組時，會在一個區段合併它們並依字母順序排序它們。  這表示使用者定義的全域初始設定式 \(Visual C\+\+ 編譯器將之放入 `.CRT$XCU`\) 一定會出現在 `.CRT$XCA` 之後以及在 `.CRT$XCZ`之前。  
  
 區段看起來如下:  
  
```  
.CRT$XCA  
            __xc_a  
.CRT$XCU  
            Pointer to Global Initializer 1  
            Pointer to Global Initializer 2  
.CRT$XCZ  
            __xc_z  
```  
  
 因此， CRT 程式庫使用 `__xc_a` 和 `__xc_z` 以判斷全域初始設定式清單的開頭和結尾，因為它們在映像載入之後在記憶體中配置的方式。  
  
## 請參閱  
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)