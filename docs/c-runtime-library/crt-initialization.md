---
title: "CRT 初始化 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d472026649bbe1d72a9afba42f224b0b9159258d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crt-initialization"></a>CRT 初始化
本主題描述 CRT 如何在機器碼中初始化全域狀態。  
  
 根據預設，連結器會包含能自行提供起始程式碼的 CRT 程式庫。 此起始程式碼會初始化 CRT 程式庫，呼叫全域初始設定式，然後呼叫由使用者針對主控台應用程式所提供的 `main` 函式。  
  
## <a name="initializing-a-global-object"></a>初始化全域物件  
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
  
 根據 C/C++ 標準，`func()` 必須在執行 `main()` 之前呼叫。 但呼叫它的是誰？  
  
 其中一種判斷方式，便是在 `func()` 中設定中斷點，對應用程式進行偵錯，然後檢查堆疊。 之所以可以這麼做，是因為 CRT 原始程式碼包含在 Visual Studio 之中。  
  
 當您瀏覽堆疊上的函式時，會發現 CRT 會在一連串的函式指標之間重複循環，並會在遭遇到每個函式指標時呼叫它們。 這些函式都類似於 `func()` 或針對類別執行個體的建構函式。  
  
 CRT 會從 Visual C++ 編譯器取得函式指標清單。 當編譯器看見全域初始設定式的時候，它會在 `.CRT$XCU` 區段 (其中 `CRT` 為區段名稱，而 `XCU` 為群組名稱) 中產生動態初始設定式。 若要取得那些動態初始設定式的清單，請執行命令 **dumpbin /all main.obj**，然後搜尋 `.CRT$XCU` 區段 (當 main.cpp 已編譯為 C++，而非 C 檔案時)。 它將會類似下列內容：  
  
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
  
 CRT 會定義兩個指標：  
  
-   `__xc_a` (英文) 中的`.CRT$XCA` (英文)  
  
-   `__xc_z` (英文) 中的`.CRT$XCZ` (英文)  
  
 除了 `__xc_a` 和 `__xc_z` 之外，這兩個群組不會有任何其他定義的符號。  
  
 現在，當連結器讀取各個 `.CRT` 群組時，它會將它們結合成單一區段，並依字母順序加以排序。 這代表使用者定義的全域初始設定式 (Visual C++ 編譯器會將它置於 `.CRT$XCU` 中) 將會一律位於 `.CRT$XCA` 之後，以及 `.CRT$XCZ` 之前。  
  
 該區段將會類似下列內容：  
  
```  
.CRT$XCA  
            __xc_a  
.CRT$XCU  
            Pointer to Global Initializer 1  
            Pointer to Global Initializer 2  
.CRT$XCZ  
            __xc_z  
```  
  
 因此，基於全域初始設定式清單項目於載入映像後在記憶體中的排列方式，CRT 程式庫將能使用 `__xc_a` 和 `__xc_z` 來判斷全域初始設定式清單的開頭和結尾。  
  
## <a name="see-also"></a>請參閱  
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)