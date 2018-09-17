---
title: MASM 巨集 |Microsoft Docs
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
ms.openlocfilehash: cb436acae117c78bfa5c752b905bd3f4f910e9da
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707846"
---
# <a name="masm-macros"></a>MASM 巨集

為了簡化使用[未經處理的虛擬作業](../build/raw-pseudo-operations.md)，有一份 ksamd64.inc，可用來建立一般的程序序言和結尾中定義的巨集。

## <a name="remarks"></a>備註

|巨集|描述|
|-----------|-----------------|
|alloc_stack(n)|配置 （使用子 rsp，n） n 個位元組的堆疊框架，並會發出適當的回溯資訊 (.allocstack n)|
|save_reg reg 當地語系化|儲存靜態暫存器 reg RSP 位移位置，在堆疊上，並發出適當的回溯資訊。 (.savereg reg，loc)|
|push_reg reg|將靜態暫存器 reg 推入堆疊，並發出適當的回溯資訊。 (.pushreg reg)|
|rex_push_reg reg|使用 2 位元組推入堆疊上儲存靜態暫存器，並會發出適當的回溯的資訊 (.pushreg reg)，這應該用於推播是以確保函式是經常性存取-可修補函式中的第一個指令。|
|save_xmm128 reg 當地語系化|將的靜態，xmm 暫存器 reg 儲存 RSP 位移位置，在堆疊上，並會發出適當的回溯資訊 （.savexmm128 reg、 當地語系化）|
|set_frame reg 位移|設定框架註冊 reg，是 RSP + 位移 （使用 mp4、mov 或讓），並發出適當的回溯資訊 （.set_frame reg、 位移）|
|push_eflags|將推送 eflags pushfq 指令，並會發出適當的回溯資訊 (.alloc_stack 8)|

以下是範例函式初構與巨集的正確用法：

```asm
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