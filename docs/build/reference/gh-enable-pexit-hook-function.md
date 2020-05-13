---
title: /GH (啟用 _pexit 攔截函式)
ms.date: 11/04/2016
f1_keywords:
- _pexit
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
ms.openlocfilehash: 5382ba90f490aaa12e9e55767fdf15170a69ced5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749235"
---
# <a name="gh-enable-_pexit-hook-function"></a>/GH (啟用 _pexit 攔截函式)

在每個方法`_pexit`或函數的末尾調用函數。

## <a name="syntax"></a>語法

```
/GH
```

## <a name="remarks"></a>備註

該`_pexit`函數不是任何庫的一部分,由您`_pexit`提供的定義。

除非您計劃顯式調用`_pexit`,否則不需要提供原型。 該函數必須顯示為具有以下原型,並且必須在輸入時推送所有寄存器的內容,並在退出時彈出未更改的內容:

```cpp
void __declspec(naked) __cdecl _pexit( void );
```

`_pexit`類似於`_penter`;有關如何編寫`_pexit`函數的示例,請參閱[/Gh(啟用_penter挂鉤函數)。](gh-enable-penter-hook-function.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] **** 資料夾。

1. 按一下 [命令列] **** 屬性頁。

1. 在 [其他選項] **** 方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
