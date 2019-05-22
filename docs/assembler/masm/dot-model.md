---
title: .MODEL
ms.date: 08/30/2018
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: c409bf10a2f863c380cda6b4822583ffb3787da6
ms.sourcegitcommit: 61121faf879cc581a4d39e4baccabf7cf1f673a5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934096"
---
# <a name="model"></a>.MODEL

將程式記憶體模型初始化。

## <a name="syntax"></a>語法

> .MODEL memorymodel [[, langtype]] [[, stackoption]]

### <a name="parameters"></a>參數

*memorymodel*<br/>
決定程式碼大小與資料點的必要參數。

*langtype*<br/>
為程序及公用符號設定呼叫及命名慣例的選擇性參數。

*stackoption*<br/>
選擇性參數。

若 *memorymodel* 為 `FLAT`，就不會使用 *stackoption*。

指定 `NEARSTACK` 會將堆疊區段與資料一併分成單一實體區段 (`DGROUP`)。 系統會假設堆疊區段暫存器 (`SS`) 擁有與資料區段暫存器 (`DS`) 相同的位址。 `FARSTACK` 不會以 `DGROUP` 為堆疊分組；因此 `SS` 不等於 `DS`。

## <a name="remarks"></a>備註

.`MODEL` 不會用於 [x64 的 MASM (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md)。

下表列出了以 16 位元和 32 位元平台為目標時，各個參數可能的值：

|參數|32 位元值|16 位元值 (支援較早的 16 位元開發)|
|---------------|--------------------|----------------------------------------------------------------|
|*memorymodel*|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|
|*langtype*|`C`、 `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|
|*stackoption*|未使用|`NEARSTACK`、 `FARSTACK`|

## <a name="code"></a>程式碼

如需 MASM 相關範例，請從 [Visual C++ Samples and Related Documentation for Visual Studio 2010](https://go.microsoft.com/fwlink/p/?linkid=178749) (適用於 Visual Studio 2010 的 Visual C++ 範例及相關文件) 下載編譯器範例。

下列範例示範 `.MODEL` 指示詞的用法。

## <a name="example"></a>範例

```asm
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

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>
