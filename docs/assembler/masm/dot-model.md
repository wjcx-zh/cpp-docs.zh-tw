---
title: .MODEL
ms.date: 11/05/2019
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: bfc114a6e71c0eb0ae70005c2657871b6c9e9692
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398103"
---
# <a name="model-32-bit-masm"></a>.MODEL (32-bit MASM)

將程式記憶體模型初始化。 (32-bit MASM only.)

## <a name="syntax"></a>語法

> **.MODEL** *memory-model* ⟦ __,__ *language-type*⟧ ⟦ __,__ *stack-option*⟧

### <a name="parameters"></a>參數

*memory-model*\
決定程式碼大小與資料點的必要參數。

*language-type*\
為程序及公用符號設定呼叫及命名慣例的選擇性參數。

*stack-option*\
選擇性參數。

*stack-option* is not used if *memory-model* is **FLAT**.

Specifying **NEARSTACK** groups the stack segment into a single physical segment (**DGROUP**) along with data. The stack segment register (**SS**) is assumed to hold the same address as the data segment register (**DS**). **FARSTACK** does not group the stack with **DGROUP**; thus **SS** does not equal **DS**.

## <a name="remarks"></a>備註

**.MODEL** is not used in [MASM for x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

下表列出了以 16 位元和 32 位元平台為目標時，各個參數可能的值：

|參數|32 位元值|16 位元值 (支援較早的 16 位元開發)|
|---------------|--------------------|----------------------------------------------------------------|
|*memory-model*|**FLAT**|**TINY**, **SMALL**, **COMPACT**, **MEDIUM**, **LARGE**, **HUGE**, **FLAT**|
|*language-type*|**C**, **STDCALL**|**C**, **BASIC**, **FORTRAN**, **PASCAL**, **SYSCALL**, **STDCALL**|
|*stack-option*|未使用|**NEARSTACK**, **FARSTACK**|

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

## <a name="see-also"></a>請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)
