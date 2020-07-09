---
title: /Gh (啟用 _penter 攔截函式)
description: 描述呼叫所提供 _penter 函數的/Gh 編譯器選項。
ms.date: 07/06/2020
f1_keywords:
- _penter
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
ms.openlocfilehash: 96597d964e6a341aa25f4d52d34974949eb7b096
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058577"
---
# <a name="gh-enable-_penter-hook-function"></a>/Gh (啟用 _penter 攔截函式)

導致在 `_penter` 每個方法或函式的開頭呼叫函式。

## <a name="syntax"></a>語法

> **`/Gh`**

## <a name="remarks"></a>備註

`_penter`函數不是任何程式庫的一部分。 您必須提供的定義 `_penter` 。

除非您打算明確呼叫 `_penter` ，否則您不需要提供原型。 函式必須推送專案上所有暫存器的內容，並在結束時將未變更的內容快顯。 它必須看起來像具有下列原型：

```cpp
void __declspec(naked) __cdecl _penter( void );
```

64位專案無法使用此宣告。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 開啟 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> ＞。

## <a name="example"></a>範例

使用 **/Gh**編譯時，下列程式碼 `_penter` 會顯示呼叫兩次的方式：在進入函式時， `main` 以及在進入函式時一次 `x` 。 這個範例是由兩個原始檔所組成，分別進行編譯。

```cpp
// local_penter.cpp
// compile with: cl /EHsc /c local_penter.cpp
// processor: x86
#include <stdio.h>

extern "C" void __declspec(naked) __cdecl _penter( void ) {
   _asm {
      push eax
      push ebx
      push ecx
      push edx
      push ebp
      push edi
      push esi
    }

   printf_s("\nIn a function!");

   _asm {
      pop esi
      pop edi
      pop ebp
      pop edx
      pop ecx
      pop ebx
      pop eax
      ret
    }
}
```

```cpp
// Gh_compiler_option.cpp
// compile with: cl /EHsc /Gh Gh_compiler_option.cpp local_penter.obj
// processor: x86
#include <stdio.h>

void x() {}

int main() {
   x();
}
```

執行時， `_penter` 會在進入和時呼叫區域函 `main` 式 `x` ：

```Output

In a function!
In a function!
```

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[`/GH`（啟用 _pexit 攔截函式）](gh-enable-pexit-hook-function.md)
