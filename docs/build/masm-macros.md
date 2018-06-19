---
title: MASM 巨集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 403220306a2585b1506a990664eaa2ec8f2ac1a3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368690"
---
# <a name="masm-macros"></a>MASM 巨集
為了簡化使用[未經處理的虛擬作業](../build/raw-pseudo-operations.md)，有一組巨集，ksamd64.inc，可用來建立一般的程序序言和結尾中定義。  
  
## <a name="remarks"></a>備註  
  
|巨集|描述|  
|-----------|-----------------|  
|alloc_stack(n)|配置堆疊框架的 n 個位元組 （使用 n 的 sub rsp），並會發出適當的回溯資訊 (.allocstack n)|  
|save_reg reg 當地語系化|儲存靜態暫存器 reg RSP 位移位置，在堆疊上，並會發出適當的回溯資訊。 (.savereg reg，loc)|  
|push_reg reg|將靜態暫存器 reg 推送至堆疊，並發出適當的回溯資訊。 (.pushreg reg)|  
|rex_push_reg reg|使用 2 位元組推入堆疊上儲存靜態暫存器，並會發出適當的回溯函式中的第一個指令以確保函式是熱-可修補發送是否應使用此資訊 (.pushreg reg)。|  
|save_xmm128 reg 當地語系化|儲存靜態 xmm 暫存器 RSP 位移位置，在堆疊上的登錄，並會發出適當的回溯資訊 （.savexmm128 reg、 loc）|  
|set_frame reg 位移|設定框架暫存器 reg，到能 RSP + 位移 （使用 mov、 或 lea），並發出適當的回溯資訊 （.set_frame reg、 位移）|  
|push_eflags|與 pushfq 指示 eflags 推播通知，並發出適當的回溯資訊 (.alloc_stack 8)|  
  
 以下是範例函式初構具有適當的使用方式的巨集：  
  
```  
SkFrame struct   
Fill    dq ?; fill to 8 mod 16   
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
  
## <a name="see-also"></a>另請參閱  
 [MASM 的回溯協助程式](../build/unwind-helpers-for-masm.md)