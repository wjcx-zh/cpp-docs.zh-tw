---
title: /Gh (啟用 _penter 攔截函式)
ms.date: 11/04/2016
f1_keywords:
- _penter
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
ms.openlocfilehash: 9a2b662ac8cbada8893a8799e35f1e51250baf62
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416523"
---
# <a name="gh-enable-penter-hook-function"></a>/Gh (啟用 _penter 攔截函式)

導致呼叫`_penter`開頭的每個方法或函式的函式。

## <a name="syntax"></a>語法

```
/Gh
```

## <a name="remarks"></a>備註

`_penter`函式不是任何文件庫的一部分，且它可以決定是否要提供的定義`_penter`。

除非您計劃會明確地呼叫`_penter`，您不需要提供原型。 如同它已有下列的原型，並必須推送的所有暫存器內容項目，並在結束 pop 未變更的內容，必須出現函式：

```
void __declspec(naked) __cdecl _penter( void );
```

這個宣告不是適用於 64 位元專案。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="example"></a>範例

下列程式碼，以編譯時 **/Gh**，顯示如何`_penter`兩次; 呼叫一次輸入函式時`main`一次輸入函式時`x`。

```cpp
// Gh_compiler_option.cpp
// compile with: /Gh
// processor: x86
#include <stdio.h>
void x() {}

int main() {
   x();
}

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

```Output
In a function!
In a function!
```

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
