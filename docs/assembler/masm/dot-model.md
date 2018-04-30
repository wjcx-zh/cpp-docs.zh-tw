---
title: .MODEL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .MODEL
dev_langs:
- C++
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2814b1b6cc4483807f77989ff4fbb70929400d6e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="model"></a>.MODEL
初始化程式記憶體模型。  
  
## <a name="syntax"></a>語法  
  
```  
.MODEL memorymodel [[, langtype]] [[, stackoption]]  
```  
  
#### <a name="parameters"></a>參數  
 `memorymodel`  
 必要的參數會決定程式碼和資料指標的大小。  
  
 `langtype`  
 設定程序與公用符號的呼叫和命名慣例的選擇性參數。  
  
 `stackoption`  
 選擇性參數。  
  
 `stackoption` 如果不使用`memorymodel`是`FLAT`。  
  
 指定`NEARSTACK`分組到單一實體區段的堆疊區段 (`DGROUP`) 以及資料。 堆疊區段暫存器 (`SS`) 會假設為保存的資料區段暫存器相同的位址 (`DS`)。 `FARSTACK` 不會分組具有堆疊`DGROUP`; 因此`SS`不等於`DS`。  
  
## <a name="remarks"></a>備註  
 .`MODEL` 不會用於[MASM (ml64.exe) x64](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
 16 位元和 32 位元平台為目標時下, 表列出每個參數的可能值：  
  
|參數|32 位元值|16 位元值 （先前的 16 位元開發支援）|  
|---------------|--------------------|----------------------------------------------------------------|  
|`memorymodel`|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|  
|`langtype`|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|  
|`stackoption`|未使用|`NEARSTACK`, `FARSTACK`|  
  
## <a name="code"></a>程式碼  
 如需 MASM 相關範例，編譯器範例下載[Visual c + + 範例和相關文件的 Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749)。  
  
 下列範例示範如何使用`.MODEL`指示詞。  
  
## <a name="example"></a>範例  
  
```  
; file simple.asm  
; For x86 (32-bit), assemble with debug information:   
;   ml -c -Zi simple.asm  
; For x64 (64-bit), assemble with debug information:   
;   ml64 -c -DX64 -Zi simple.asm  
;  
; In this sample, the 'X64' define excludes source not used   
;  when targeting the x64 architecture  
  
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
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)   
 [Visual c + + 範例和相關文件的 Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749)