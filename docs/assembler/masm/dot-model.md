---
title: .MODEL
ms.date: 08/30/2018
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: 5c7d5a1cfe16ef3cb1d79617133cd1ceccdfb78c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633503"
---
# <a name="model"></a>.MODEL

初始化程式記憶體內部模型。

## <a name="syntax"></a>語法

> .模型 memorymodel [[，langtype]] [[，stackoption]]

### <a name="parameters"></a>參數

*memorymodel*<br/>
判斷程式碼和資料指標的大小的必要的參數。

*langtype*<br/>
設定程序和公用符號的呼叫和命名慣例的選擇性參數。

*stackoption*<br/>
選擇性參數。

*stackoption*如果不使用*memorymodel*是`FLAT`。

指定`NEARSTACK`堆疊區段組成單一的實體區段 (`DGROUP`) 以及資料。 堆疊區段暫存器 (`SS`) 會假設為保留資料區段註冊相同的位址 (`DS`)。 `FARSTACK` 不會分組堆疊`DGROUP`，因此`SS`不等於`DS`。

## <a name="remarks"></a>備註

.`MODEL` 不會用於[MASM (ml64.exe) x64 的](../../assembler/masm/masm-for-x64-ml64-exe.md)。

16 位元和 32 位元的平台為目標時下, 表將列出每個參數的可能值：

|參數|32 位元值|16 位元值 （較早的 16 位元開發支援）|
|---------------|--------------------|----------------------------------------------------------------|
|*memorymodel*|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|
|*langtype*|`C`、 `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|
|*stackoption*|未使用|`NEARSTACK`、 `FARSTACK`|

## <a name="code"></a>程式碼

如需 MASM 相關的範例中，編譯器範例下載[Visual c + + 範例和相關的文件適用於 Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749)。

下列範例示範如何使用`.MODEL`指示詞。

## <a name="example"></a>範例

```asm
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

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>

