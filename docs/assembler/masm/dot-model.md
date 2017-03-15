---
title: ".MODEL | Microsoft Docs"
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
  - ".MODEL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".MODEL directive"
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .MODEL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

初始化程式的記憶體模型。  
  
## 語法  
  
```  
.MODEL memorymodel [[, langtype]] [[, stackoption]]  
```  
  
#### 參數  
 `memorymodel`  
 必要的參數，以判斷程式碼和資料指標的大小。  
  
 `langtype`  
 設定程序和公用符號的呼叫，並命名慣例的選擇性參數。  
  
 `stackoption`  
 選擇性參數。  
  
 `stackoption`is not used if `memorymodel` is `FLAT`.  
  
 指定`NEARSTACK`成單一實體區段群組堆疊區段 \(`DGROUP`\) 的資料一起。  堆疊區段暫存器 \(`SS`\) 會被假設為保留的資料區段暫存器與相同的位址 \(`DS`\)。  `FARSTACK`未群組與堆疊`DGROUP`。 因此`SS`不等於`DS`。  
  
## 備註  
 .`MODEL`不會用於[MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
 以 16 位元和 32 位元平台為目標時下, 表列出可能的值為每個參數：  
  
|參數|32 位元值|16 位元值 \(較早的 16 位元程式開發的支援\)|  
|--------|------------|---------------------------------|  
|`memorymodel`|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|  
|`langtype`|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|  
|`stackoption`|未使用|`NEARSTACK`, `FARSTACK`|  
  
## 程式碼  
 如 MASM 相關範例，下載編譯器範例從[Visual C\+\+ 範例和相關文件的 Visual Studio 2010年](完整.嗎？LinkID%20=%20178749)。  
  
 下列範例示範如何使用`.MODEL`指示詞。  
  
## 範例  
  
```  
; file simple.asm  
; For x86 (32-bit), assemble with debug information:   
;   ml -c -Zi simple.asm  
; For x64 (64-bit), assemble with debug information:   
;   ml64 -c -DX64 -Zi simple.asm  
;  
; In this sample, the 'X64' define excludes source not used   
;  when targeting the x64 architecture  
  
ifndef X64  
.686p  
.XMM  
.model flat, C  
endif  
  
.data  
; user data  
  
.code  
; user code  
  
fxn PROC public  
  xor eax, eax ; zero function return value  
  ret  
fxn ENDP  
  
end  
```  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)   
 [Visual C\+\+ 範例和相關文件的 Visual Studio 2010年](完整.嗎？LinkID%20=%20178749)