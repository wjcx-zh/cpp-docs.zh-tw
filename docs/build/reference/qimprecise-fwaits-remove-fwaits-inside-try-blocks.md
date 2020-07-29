---
title: /Qimprecise_fwaits (移除 Try 區域內的 fwaits)
ms.date: 11/04/2016
f1_keywords:
- /Qimprecise_fwaits
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
ms.openlocfilehash: 424feda66f6925cb305256249101ea4013e3090f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232673"
---
# <a name="qimprecise_fwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (移除 Try 區域內的 fwaits)

`fwait` **`try`** 當您使用[/fp： except](fp-specify-floating-point-behavior.md)編譯器選項時，會移除區塊內部的命令。

## <a name="syntax"></a>語法

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>備註

如果未同時指定 **/fp： except** ，這個選項不會有任何作用。 如果您指定 [ **/fp： except** ] 選項，編譯器會 `fwait` 在區塊中的每一行程式碼前後插入一個命令 **`try`** 。 如此一來，編譯器就可以識別產生例外狀況的特定程式程式碼。 **/Qimprecise_fwaits**移除內部 `fwait` 指示，只保留區塊的等候 **`try`** 。 這會改善效能，但是編譯器只能說出哪個 **`try`** 區塊造成例外狀況，而不是哪一行。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] **** 資料夾。

1. 按一下 [命令列] **** 屬性頁。

1. 在 [其他選項] **** 方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> ＞。

## <a name="see-also"></a>另請參閱

[/Q 選項（低層級作業）](q-options-low-level-operations.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
