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
# <a name="model-32-bit-masm"></a>.MODEL （32位 MASM）

將程式記憶體模型初始化。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> **.模型***記憶體-模型*⟦ __，__ *語言類型*⟧⟦ __，__ *堆疊選項*⟧

### <a name="parameters"></a>參數

*記憶體模型*\
決定程式碼大小與資料點的必要參數。

*語言類型*\
為程序及公用符號設定呼叫及命名慣例的選擇性參數。

*堆疊選項*\
選擇性參數。

如果*記憶體模型*是**平面**的，則不會使用*堆疊選項*。

指定**NEARSTACK**會將堆疊區段與資料一起分組到單一實體區段（**DGROUP**）。 堆疊區段暫存器（**SS**）會假設為與資料區段暫存器（**DS**）保持相同的位址。 **FARSTACK**不會使用**DGROUP**將堆疊分組;因此， **SS**不等於**DS**。

## <a name="remarks"></a>備註

**.MODEL**不會用於[MASM for x64 （ml64 .exe）](../../assembler/masm/masm-for-x64-ml64-exe.md)。

下表列出了以 16 位元和 32 位元平台為目標時，各個參數可能的值：

|參數|32 位元值|16 位元值 (支援較早的 16 位元開發)|
|---------------|--------------------|----------------------------------------------------------------|
|*記憶體模型*|**還是**|小規模、**小型**、**精簡**、**中型**、**大型**、**龐大**、**平面**|
|*語言類型*|**C**、 **STDCALL**|**C**、**基本**、 **FORTRAN**、 **PASCAL**、 **SYSCALL**、 **STDCALL**|
|*堆疊-選項*|未使用|**NEARSTACK**、 **FARSTACK**|

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

[指示詞參考](../../assembler/masm/directives-reference.md)
