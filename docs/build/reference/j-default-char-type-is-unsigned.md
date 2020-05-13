---
title: /J (預設 char 類型為 unsigned)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
ms.openlocfilehash: 7bcf0f2eb2bef08757250999d0a6696b256fb15c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322190"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (預設 char 類型為 unsigned)

將預設 `char` 類型從 `signed char` 變更為 `unsigned char`，而且 `char` 類型在擴展為 `int` 類型時，是以零擴充的。

## <a name="syntax"></a>語法

```
/J
```

## <a name="remarks"></a>備註

如果`char`值顯式聲明`signed`為 **,/J**選項不會影響該值,並且當該值`int`被擴展為 類型時,該值將符號擴展。

**/J**選項`_CHAR_UNSIGNED`定義`#ifndef`,`char`用於在

ANSI C 和C++不需要`char`該類型的特定實現。 當您使用字元數據時,此選項非常有用,這些數據最終將轉換為英語以外的語言。

> [!NOTE]
> 如果您搭配 ATL/MFC 使用這個編譯器選項，可能會產生錯誤。 雖然您可以透過定義 `_ATL_ALLOW_CHAR_UNSIGNED` 停用這個錯誤，這個解決方法卻不支援而且未必可行。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 在**解決方案資源管理員**中,開啟專案的快捷方式選單,然後選擇**屬性**。

1. 在「項目**屬性頁」** 對話框中,在 **「設定屬性**」 的左邊窗格中,展開**C/C++,** 然後選擇**命令列**。

1. 在「**附加選項」** 窗格中,指定 **/J**編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)
