---
title: "/Gd、/Gr、/Gv、/Gz (呼叫慣例) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/gr"
  - "/Gv"
  - "/gz"
  - "/Gd"
  - "VC.Project.VCCLCompilerTool.CallingConvention"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gd 編譯器選項 [C++]"
  - "/Gr 編譯器選項 [C++]"
  - "/Gv 編譯器選項 [C++]"
  - "/Gz 編譯器選項 [C++]"
  - "Gd 編譯器選項 [C++]"
  - "-Gd 編譯器選項 [C++]"
  - "Gr 編譯器選項 [C++]"
  - "-Gr 編譯器選項 [C++]"
  - "Gv 編譯器選項 [C++]"
  - "-Gv 編譯器選項 [C++]"
  - "Gz 編譯器選項 [C++]"
  - "-Gz 編譯器選項 [C++]"
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Gd、/Gr、/Gv、/Gz (呼叫慣例)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些選項決定函式引數推入至堆疊上的順序；不管是呼叫端函式或是被呼叫的函式在呼叫結束時從堆疊移除引數；以及編譯器用來辨認各個函式的名稱裝飾慣例。  
  
## 語法  
  
```  
/Gd  
/Gr  
/Gv  
/Gz  
```  
  
## 備註  
 除了 C\+\+ 成員函式和標記了 [\_\_stdcall](../../cpp/stdcall.md)、[\_\_fastcall](../../cpp/fastcall.md) 或 [\_\_vectorcall](../../cpp/vectorcall.md) 的函式以外，**\/Gd** \(預設設定\) 會指定所有函式的 [\_\_cdecl](../../cpp/cdecl.md) 呼叫慣例 \(Calling Convention\)。  
  
 除了 C\+\+ 成員函式、名為 `main` 的函式和標記了 `__cdecl`、`__stdcall` 或 `__vectorcall` 的函式以外，**\/Gr** 會指定所有函式的 `__fastcall` 呼叫慣例 \(Calling Convention\)。  所有 `__fastcall` 函式必須有原型。  這個呼叫慣例僅供以 x86 為目標的編譯器使用，以其他架構為目標的編譯器會忽略它。  
  
 除了 C\+\+ 成員函式、名為 `main` 的函式和標記了 `__cdecl`、`__fastcall` 或 `__vectorcall` 的函式以外，**\/Gz** 會指定所有函式的 `__stdcall` 呼叫慣例 \(Calling Convention\)。  所有 `__stdcall` 函式必須有原型。  這個呼叫慣例僅供以 x86 為目標的編譯器使用，以其他架構為目標的編譯器會忽略它。  
  
 除了 C\+\+ 成員函式，名為 main 的函式、有 `vararg` 變數引數清單的函式，或是標記 `__cdecl`, `__stdcall` 或  `__fastcall` 屬性衝突的函式，**\/Gv** 會指定所有函式的 `__vectorcall` 呼叫慣例。  這個呼叫慣例只適用於支援 \/arch:SSE2 以上的 x86 和 x64 架構，以 ARM 架構為目標的編譯器會忽略它。  
  
 採用數目不定之引數的函式必須標記 `__cdecl`。  
  
 **\/Gd**、**\/Gr**、**\/Gv** 及 **\/Gz**，與 [\/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) 或 **\/clr:pure** 不相容。  
  
> [!NOTE]
>  如果是 x86 處理器，C\+\+ 成員函式預設會使用 [\_\_thiscall](../../cpp/thiscall.md)。  
  
 對所有處理器來說，明確標記為 `__cdecl`、`__fastcall`、`__vectorcall` 或 `__stdcall` 的成員函式會使用指定的呼叫慣例 \(如果未在該架構上忽略的話\)。  接受可變引數數目的成員函式永遠使用 `__cdecl` 呼叫慣例。  
  
 這些編譯器選項對於 C\+\+ 方法和函式的名稱裝飾 \(Name Decoration\) 沒有作用。  除非宣告為 `extern "C"`，否則 C\+\+ 方法和函式會使用不同的名稱裝飾配置。  如需詳細資訊，請參閱[裝飾名稱](../../build/reference/decorated-names.md)。  
  
 如需關於呼叫慣例的詳細資訊，請參閱[呼叫慣例](../../cpp/calling-conventions.md)。  
  
## \_\_cdecl 專屬資訊  
 x86 處理器上，所有函式引數都是在堆疊上由右至左傳遞。  在 x64 和 ARM 結構中，有些引數是由暫存器傳遞，而其他則是在堆疊上由右至左傳遞。  發出呼叫的常式會從堆疊中顯示引數。  
  
 如果是 C，`__cdecl` 命名慣例是使用函式名稱，前面加上底線 \(`_`\)；不會執行大小寫轉譯。  除非宣告為 `extern "C"`，否則 C\+\+ 函式會使用不同的名稱裝飾配置。  如需詳細資訊，請參閱[裝飾名稱](../../build/reference/decorated-names.md)。  
  
## \_\_fastcall 專屬資訊  
 有些 `__fastcall` 函式的引數是在暫存器中傳遞 \(在 x86 處理器上有 ECX 和 EDX\)，其餘的則是從右至左推入到堆疊上。  被呼叫的常式會在返回前將這些引數由堆疊取出。  通常，**\/Gr** 會縮短執行時間。  
  
> [!NOTE]
>  對任何以內嵌組譯碼語言撰寫的函式使用 `__fastcall` 呼叫慣例時要特別留意。  您對暫存器的使用可能會與編譯器對它們的使用衝突。  
  
 如果是 C，`__fastcall` 命名慣例是使用函式名稱，前面加上 at 符號 \(`@`\)，後面跟著以位元組為單位的函式引數大小。  不會執行大小寫轉譯。  編譯器會使用這個範本做為命名慣例：  
  
```c  
@function_name@number  
```  
  
 使用 `__fastcall` 命名慣例時，請使用標準 Include 檔案。  否則您將會得到未解析的外部參考。  
  
## \_\_stdcall 專屬資訊  
 `__stdcall` 函式的引數會由右至左推入堆疊，而且被呼叫的函式會在返回前將這些引數由堆疊取出。  
  
 如果是 C，`__stdcall` 命名慣例是使用函式名稱，前面加上底線 \( `_` \)，後面跟著 at 符號 \(@\) 和以位元組為單位的函式引數大小。  不會執行大小寫轉譯。  編譯器會使用這個範本做為命名慣例：  
  
```c  
_functionname@number  
```  
  
## \_\_vectorcall 特定  
 `__vectorcall` 函式的整數引數由值傳遞，最多使用兩個 \(在 x86\) 或四個 \(在 x64\) 整數暫存器，以及六個 XMM 暫存器為浮點和巡覽值，其他在堆疊中從右至左傳遞。  呼叫的函式會在傳回前清除堆疊。  向量和浮點傳回值是在 XMM0 中傳回。  
  
 如果是 C，`__vectorcall` 命名慣例是使用函式名稱，後面跟隨兩個 @ 記號 \(@@\)，再加上函式引數大小 \(以位元組為單位\)。  不會執行大小寫轉譯。  編譯器會使用這個範本做為命名慣例：  
  
```c  
functionname@@number  
```  
  
### To set this compiler option in the Visual Studio development environment  
  
1.  Open the project's **Property Pages** dialog box.  For details, see [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md).  
  
2.  Select the **C\/C\+\+** folder.  
  
3.  Select the **Advanced** property page.  
  
4.  Modify the **Calling Convention** property.  
  
### To set this compiler option programmatically  
  
-   See <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)