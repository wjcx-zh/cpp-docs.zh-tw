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
ms.openlocfilehash: 87815b5f0e0450b84acbe3c35b7ef4f31216ec72
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749288"
---
# <a name="gh-enable-_penter-hook-function"></a>/Gh (啟用 _penter 攔截函式)

在每個方法或函數的`_penter`開頭對函數進行調用。

## <a name="syntax"></a>語法

```
/Gh
```

## <a name="remarks"></a>備註

該`_penter`函數不是任何庫的一部分,由您`_penter`提供的定義。

除非您計劃顯式調用`_penter`,否則不需要提供原型。 該函數必須顯示為具有以下原型,並且必須在輸入時推送所有寄存器的內容,並在退出時彈出未更改的內容:

```cpp
void __declspec(naked) __cdecl _penter( void );
```

此聲明不適用於 64 位元專案。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] **** 資料夾。

1. 按一下 [命令列] **** 屬性頁。

1. 在 [其他選項] **** 方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>＞。

## <a name="example"></a>範例

使用 **/Gh**編譯時,以下代碼顯示`_penter`了如何 調用兩次;一次,當`main`進入函數和一`x`次 當進入函數。

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

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
