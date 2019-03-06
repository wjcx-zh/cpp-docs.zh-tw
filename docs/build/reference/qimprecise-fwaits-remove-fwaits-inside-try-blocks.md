---
title: /Qimprecise_fwaits (移除 Try 區域內的 fwaits)
ms.date: 11/04/2016
f1_keywords:
- /Qimprecise_fwaits
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
ms.openlocfilehash: 3f2a0e6bc28fb812e087a689716be6119640ffca
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422131"
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (移除 Try 區域內的 fwaits)

移除`fwait`命令的內部`try`當您使用時封鎖[/fp： 除了](../../build/reference/fp-specify-floating-point-behavior.md)編譯器選項。

## <a name="syntax"></a>語法

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>備註

如果此選項會有任何作用 **/fp： 除了**也未指定。 如果您指定 **/fp： 除了**選項，編譯器會插入`fwait`周圍每一行程式碼中命令`try`區塊。 如此一來，編譯器能夠識別特定一行程式碼會產生例外狀況。 **/Qimprecise_fwaits**移除內部`fwait`的指示，離開周圍，等待`try`區塊。 這樣可改善效能，但編譯器只能說這`try`區塊會造成例外狀況，而不是那一行。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/Q 選項 (低階運算)](../../build/reference/q-options-low-level-operations.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
