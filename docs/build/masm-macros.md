---
title: "MASM 巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# MASM 巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為了要簡化 [未經處理的虛擬作業](../build/raw-pseudo-operations.md) 的使用方式，ksamd64.inc 中定義了一組巨集，可以用來建立典型的程序初構 \(Prologue\) 和終解 \(Epilogue\)。  
  
## 備註  
  
|巨集|描述|  
|--------|--------|  
|alloc\_stack\(n\)|配置 n 個位元組的堆疊框架 \(使用 sub rsp, n\)，並發出適當的回溯資訊 \(.allocstack n\)|  
|save\_reg reg, loc|將堆疊上的靜態 \(Nonvolatile\) 暫存器 reg 儲存到 RSP 位移 loc，並發出適當的回溯資訊  \(.savereg reg, loc\)|  
|push\_reg reg|推入堆疊上的靜態暫存器 reg，並發出適當的回溯資訊  \(.pushreg reg\)|  
|rex\_push\_reg reg|使用 2 位元組推入，儲存為靜態暫存器堆疊，，並發出適當的回溯資訊 \(.pushreg reg\) 應該使用這個，則推入是函式中的第一個指令確保函式為作用中 patchable。|  
|save\_xmm128 reg, loc|將堆疊上的靜態 XMM 暫存器 reg 儲存到 RSP 位移 loc，並發出適當的回溯資訊 \(.savexmm128 reg, loc\)|  
|set\_frame reg, offset|將框架暫存器 reg 設定為 RSP \+ 位移 \(使用 mov 或 lea\)，並發出適當的回溯資訊 \(.set\_frame reg, offset\)|  
|push\_eflags|使用 pushfq 指令推入 eflags，並發出適當的回溯資訊 \(.alloc\_stack 8\)|  
  
 以下是函式初構的範例，其中具有巨集的正確用法：  
  
```  
SkFrame struct   
Fill    dq ?; fill to 8 mod 16   
SavedRdi dq ?; saved register RDI   
SavedRsi dq ?; saved register RSI   
SkFrame ends  
  
sampleFrame struct  
Filldq?; fill to 8 mod 16  
SavedRdidq?; Saved Register RDI   
SavedRsi  dq?; Saved Register RSI  
sampleFrame ends  
  
sample2 PROC FRAME  
alloc_stack(sizeof sampleFrame)  
save_reg rdi, sampleFrame.SavedRdi  
save_reg rsi, sampleFrame.SavedRsi  
.end_prolog  
  
; function body  
  
mov rsi, sampleFrame.SavedRsi[rsp]  
mov rdi, sampleFrame.SavedRdi[rsp]  
  
; Here’s the official epilog  
  
add rsp, (sizeof sampleFrame)  
ret  
sample2 ENDP  
```  
  
## 請參閱  
 [MASM 的回溯 Helper](../build/unwind-helpers-for-masm.md)