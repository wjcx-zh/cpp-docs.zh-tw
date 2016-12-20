---
title: "MASM for x64 (ml64.exe) | Microsoft Docs"
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
  - "ml64.exe"
  - "ml"
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# MASM for x64 (ml64.exe)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ml64.exe 是組譯工具可接受[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]組合語言。  Ml64.exe 編譯器選項的相關資訊，請參閱[ML and ML64 Command\-Line Reference](../../assembler/masm/ml-and-ml64-command-line-reference.md)。  
  
 不支援內嵌 ASM [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]。  使用 MASM 或編譯器內建函式 \([x64 Intrinsics](http://msdn.microsoft.com/zh-tw/5d1f5d3e-156e-4ebf-932e-fd09be7ced62)\)。  
  
 兩種解決方法是使用 MASM \(它完全支援 x64\) 和編譯器內建的另一個組件。  新增了許多內建函式，以便讓客戶使用的函式的特殊指令 \(例如：  有權限，位元掃描\/測試，連鎖欸\)在以跨平台的方式儘可能靠近。  
  
## ml64 的特定指示詞  
 使用 ml64.exe 中的下列指示詞：  
  
-   [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)  
  
-   [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)  
  
-   [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)  
  
-   [.PUSHREG](../../assembler/masm/dot-pushreg.md)  
  
-   [.SAVEREG](../../assembler/masm/dot-savereg.md)  
  
-   [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)  
  
-   [.SETFRAME](../../assembler/masm/dot-setframe.md)  
  
 此外， [PROC](../../assembler/masm/proc.md)指示詞已經過更新，所使用的 ml64.exe。  
  
## 32 位元位址模式 \(位址大小覆寫\)  
 如果記憶體運算元包含 32 位元暫存器，MASM 將發出的 0x67 位址大小覆寫。  例如，下列範例會導致發出的地址大小覆寫：  
  
```  
mov rax, QWORD PTR [ecx]  
mov eax, DWORD PTR [ecx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10d+0100h]  
prefetch [eax]  
movnti rax, QWORD PTR [r8d]  
```  
  
 MASM 假設如果 32 位元加上位移出現記憶體運算元單獨存在，64 位元定址無關。  目前沒有使用這種運算元的 32 位元定址的支援。  
  
 最後，混合內記憶體運算元的暫存器大小，如下列程式碼所示，將會產生錯誤。  
  
```  
mov eax, DWORD PTR [rcx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10+0100h]  
```  
  
## 請參閱  
 [Microsoft Macro Assembler Reference](../../assembler/masm/microsoft-macro-assembler-reference.md)