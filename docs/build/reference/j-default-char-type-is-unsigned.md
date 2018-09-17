---
title: -J (預設 char 類型為 unsigned) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
dev_langs:
- C++
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 400985751d9ceebf7cc2c5f632cb33c5ba847bfe
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714281"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (預設 char 類型為 unsigned)

將預設 `char` 類型從 `signed char` 變更為 `unsigned char`，而且 `char` 類型在擴展為 `int` 類型時，是以零擴充的。

## <a name="syntax"></a>語法

```
/J
```

## <a name="remarks"></a>備註

如果`char`值明確宣告為`signed`，則 **/J**選項不會影響，且值為正負號擴充時擴展為`int`型別。

**/J**選項會定義`_CHAR_UNSIGNED`，這會搭配`#ifndef`LIMITS.h 檔案來定義預設值的範圍中`char`型別。

ANSI C 和 c + + 不需要的特定實作`char`型別。 當您使用將最終會翻譯成英文以外語言的字元資料時，這個選項非常有用的。

> [!NOTE]
>  如果您搭配 ATL/MFC 使用這個編譯器選項，可能會產生錯誤。 雖然您可以透過定義 `_ATL_ALLOW_CHAR_UNSIGNED` 停用這個錯誤，這個解決方法卻不支援而且未必可行。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **屬性**]。

1. 在專案中**屬性頁**下方的左窗格中的對話方塊中，**組態屬性**，展開**C/c + +** ，然後選取**命令列**.

1. 在 **其他選項**窗格中，指定 **/J**編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[使用專案屬性](../../ide/working-with-project-properties.md)