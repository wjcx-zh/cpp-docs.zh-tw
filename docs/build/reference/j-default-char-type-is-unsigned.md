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
ms.openlocfilehash: d95fed3d9af81d89ac03a52a1e6433786118430e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223833"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (預設 char 類型為 unsigned)

將預設 **`char`** 類型從變更 **`signed char`** 為 **`unsigned char`** ，而且 **`char`** 當它擴展為類型時，此類型會以零擴充 **`int`** 。

## <a name="syntax"></a>語法

```
/J
```

## <a name="remarks"></a>備註

如果將 **`char`** 值明確宣告為 **`signed`** ， **/j**選項不會影響它，而當它擴展為類型時，此值會以正負號擴充 **`int`** 。

**/J**選項會定義 `_CHAR_UNSIGNED` ，它會 `#ifndef` 在限制 .h 檔案中用來定義預設類型的範圍 **`char`** 。

ANSI C 和 c + + 不需要類型的特定執行 **`char`** 。 當您使用的字元資料最終會轉譯成英文以外的語言時，這個選項就很有用。

> [!NOTE]
> 如果您搭配 ATL/MFC 使用這個編譯器選項，可能會產生錯誤。 雖然您可以透過定義 `_ATL_ALLOW_CHAR_UNSIGNED` 停用這個錯誤，這個解決方法卻不支援而且未必可行。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 在**方案總管**中，開啟專案的快捷方式功能表，然後選擇 [**屬性**]。

1. 在 [專案**屬性頁**] 對話方塊的左窗格中，展開 [設定**屬性**] 底下的 [ **C/c + +** ]，然後選取 [**命令列**]。

1. 在 [**其他選項**] 窗格中，指定 **/j**編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)
