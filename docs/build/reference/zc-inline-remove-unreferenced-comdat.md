---
title: "/Zc:inline (移除未參考的 COMDAT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Zc:inline"
  - "VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc 編譯器選項 (C++)"
  - "/Zc:inline"
  - "Zc 編譯器選項 (C++)"
  - "-Zc 編譯器選項 (C++)"
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zc:inline (移除未參考的 COMDAT)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

移除作為 COMDAT 或僅具有內部連結的未參考函式或資料。  當指定 **\/Zc:inline** 時，編譯器要求使用內嵌資料或內嵌函式的轉譯單位還必須包括這些資料或函式的定義。  
  
## 語法  
  
```  
/Zc:inline[-]  
```  
  
## 備註  
 當指定 **\/Zc:inline** 時，編譯器不會針對未參考的 COMDAT 函式或資料，或者僅具有內部連結的函式或資料，發出符號資訊。  根據預設，這個選項為關閉狀態\(**\/Zc:inline\-**\)。  這個最佳化作業在發行組建中，或在指定 [\/OPT:REF](../../build/reference/opt-optimizations.md) 時，可簡化連結器所執行的部分工作。  當編譯器執行此最佳化作業時，可以大幅減小 .obj 檔案的大小，並提高連結器速度。  當停用最佳化作業 \([\/Od](../../build/reference/od-disable-debug.md)\) 或指定 [\/GL \(整個程式最佳化\)](../../build/reference/gl-whole-program-optimization.md) 時，不會啟用此編譯器選項。  
  
 如果指定 **\/Zc:inline**，則編譯器會強制執行 C\+\+11 需求，即在使用宣告 `inline` 的所有函式時，必須在相同轉譯單位中提供定義。  如果未指定該選項，則 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 容許使用不一致的程式碼，其可叫用已宣告 `inline` 的函式，即使看不到任何定義也一樣。  如需詳細資訊，請參閱 3.2 節和 7.1.2 節中的 C\+\+11 標準。  此編譯器選項已引入 Visual Studio 2013 Update 2。  
  
 若要使用 **\/Zc:inline** 選項，請更新不符合標準的程式碼。  此範例顯示在使用預設 **\/Zc:inline\-** 選項時，沒有定義且不符合標準之內嵌函式宣告的使用如何仍得到編譯及連結：  
  
```cpp  
// example.h  
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp  
#pragma once  
  
class Example {  
public:  
   inline void inline_call(); // declared but not defined inline  
   void normal_call();  
   Example() {};  
};  
```  
  
```cpp  
// example.cpp  
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp  
#include <stdio.h>  
#include "example.h"  
  
void Example::inline_call() {  
   printf("inline_call was called.\n");   
}  
  
void Example::normal_call() {  
   printf("normal_call was called.\n");   
   inline_call(); // with /Zc:inline-, inline_call forced into .obj file  
}  
```  
  
```cpp  
// zcinline.cpp  
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp  
#include "example.h"  
  
void main() {  
   Example example;  
   example.inline_call(); // normal call when definition unavailable  
}  
```  
  
 當啟用 **\/Zc:inline** 時，相同的程式碼會導致 [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) 錯誤，這是因為編譯器不會針對 example.obj 中的 `Example::inline_call`，發出非內嵌的程式碼主體。  這會導致 `main` 中的非內嵌呼叫，參考未定義的外部符號。  
  
 若要解決此錯誤，您可以從 `Example::inline_call` 的宣告中，移除 `inline` 關鍵字，將 `Example::inline_call` 的定義移至標頭檔，或者將 `Example` 的實作移至 main.cpp。  下一個範例會將定義移至標頭檔，在那裡，該定義對包括該標頭的任何呼叫程式都可見。  
  
```cpp  
// example2.h  
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp  
#pragma once  
#include <stdio.h>  
  
class Example2 {  
public:  
   inline void inline_call() {  
      printf("inline_call was called.\n");   
   }  
   void normal_call();  
   Example2() {};  
};  
```  
  
```cpp  
// example2.cpp  
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp  
#include "example2.h"  
  
void Example2::normal_call() {  
   printf("normal_call was called.\n");   
   inline_call();   
}  
```  
  
```cpp  
// zcinline2.cpp  
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp  
#include "example2.h"  
  
void main() {  
   Example2 example2;  
   example2.inline_call(); // normal call when definition unavailable  
}  
```  
  
 如需 Visual C\+\+ 中一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  修改 \[其他選項\] 屬性，以包括 `/Zc:inline`，然後選擇 \[確定\]。  
  
## 請參閱  
 [\/Zc \(一致性\)](../../build/reference/zc-conformance.md)