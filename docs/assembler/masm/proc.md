---
title: "PROC |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROC
dev_langs: C++
helpviewer_keywords: PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b4b8b5259e3a7e42e7eb08cb4832496a6f3c35c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="proc"></a>PROC
呼叫程序區塊的開始與結束標記*標籤*。 區塊中的陳述式可以呼叫與**呼叫**指令或[INVOKE](../../assembler/masm/invoke.md)指示詞。  
  
## <a name="syntax"></a>語法  
  
```  
  
   label PROC [[distance]] [[langtype]] [[visibility]] [[<prologuearg>]]   
[[USES reglist]] [[, parameter [[:tag]]]]...  
[FRAME [:ehandler-address] ]  
statements  
label ENDP  
```  
  
## <a name="remarks"></a>備註  
 [畫面格 [:*ehandler 位址*]] 時才有效 ml64.exe，並造成 MASM.pdata 中產生的函式表格項目，並回溯.xdata 中的資訊的函式的結構化例外狀況處理回溯行為。  
  
 當**框架**屬性，則它必須接著[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。  
  
 請參閱[MASM (ml64.exe) x64](../../assembler/masm/masm-for-x64-ml64-exe.md)如需有關使用 ml64.exe。  
  
## <a name="example"></a>範例  
  
```  
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE  
_text SEGMENT  
Example1 PROC FRAME  
   push r10  
.pushreg r10  
   push r15  
.pushreg r15  
   push rbx  
.pushreg rbx  
   push rsi  
.pushreg rsi  
.endprolog  
   ; rest of function ...  
   ret  
Example1 ENDP  
_text ENDS  
END  
```  
  
 上述程式碼將會發出函式表，並回溯資訊：  
  
```  
FileHeader->Machine 34404  
Dumping Unwind Information for file ex2.exe  
  
.pdata entry 1 0x00001000 0x00001023  
  
  Unwind data: 0x00002000  
  
    Unwind version: 1  
    Unwind Flags: None  
    Size of prologue: 0x08  
    Count of codes: 3  
    Frame register: rbp  
    Frame offset: 0x0  
    Unwind codes:  
  
      Code offset: 0x08, SET_FPREG, register=rbp, offset=0x00  
      Code offset: 0x05, ALLOC_SMALL, size=0x10  
      Code offset: 0x01, PUSH_NONVOL, register=rbp  
```  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)