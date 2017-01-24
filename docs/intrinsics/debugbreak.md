---
title: "__debugbreak | Microsoft Docs"
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
  - "__debugbreak_cpp"
  - "__debugbreak"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__debugbreak 內建"
  - "中斷點, __debugbreak 內建"
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __debugbreak
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 在您的程式碼中導致中斷點，在該位置，系統會提示使用者執行偵錯工具。  
  
## 語法  
  
```  
void __debugbreak();  
```  
  
## 需求  
  
|內建|架構|頁首|  
|--------|--------|--------|  
|`__debugbreak`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
  
## 備註  
 `__debugbreak` 編譯器內建物件與 [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297.aspx) \(英文\) 類型，是一種可導致中斷點的可移植 Win32 方法。  
  
> [!NOTE]
>  當使用 **\/clr** 進行編譯時，包含 `__debugbreak` 的函式會編譯為 MSIL。  `asm int 3` 會導致函式編譯為原生。  如需詳細資訊，請參閱[\_\_asm](../assembler/inline/asm.md)。  
  
 例如：  
  
```  
main() {  
   __debugbreak();  
}  
```  
  
 類似於：  
  
```  
main() {  
   __asm {  
      int 3  
   }  
}  
```  
  
 \(在 x86 電腦上\)。  
  
 此常式僅可作為內建常式使用。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)