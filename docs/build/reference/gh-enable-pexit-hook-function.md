---
title: /GH (啟用 _pexit 攔截函式)
description: 描述用來設定本機 _pexit 攔截函式的/GH 編譯器選項。
ms.date: 07/06/2020
f1_keywords:
- _pexit
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
ms.openlocfilehash: b8fc355503055af8b928874ced39cb8224901d3e
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058603"
---
# <a name="gh-enable-_pexit-hook-function"></a>/GH (啟用 _pexit 攔截函式)

呼叫 `_pexit` 每個方法或函數結尾的函式。

## <a name="syntax"></a>語法

> **`/GH`**

## <a name="remarks"></a>備註

`_pexit`函數不是任何程式庫的一部分。 您必須提供的定義 `_pexit` 。

除非您打算明確呼叫 `_pexit` ，否則您不需要提供原型。 函式必須推送專案上所有暫存器的內容，並在結束時將未變更的內容快顯。 它必須看起來像具有下列原型：

```cpp
void __declspec(naked) __cdecl _pexit( void );
```

64位專案無法使用此宣告。

`_pexit`類似于; 如需 `_penter` 如何撰寫函數的範例，請參閱[ `/Gh` （啟用 _penter](gh-enable-penter-hook-function.md)攔截函式） `_penter` 。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 開啟 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[`/Gh`（啟用 _penter 攔截函式）](gh-enable-penter-hook-function.md)
