---
title: /vmb、-vmg （表示方法）
ms.date: 11/04/2016
f1_keywords:
- /vmb
- /vmg
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
ms.openlocfilehash: eac41de04ec883e7b5acf26596647f912b0b1d20
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808478"
---
# <a name="vmb-vmg-representation-method"></a>/vmb、/vmg (表示方法)

選取編譯器用來代表類別成員指標的方法。

使用 **/vmb**如果您一律是之前定義類別成員的類別中宣告的指標。

使用 **/vmg**來定義類別之前宣告類別的成員的指標。 如果您在彼此參考的兩個不同類別中定義成員，則可能會發生這項需求。 對於這類相互參考的類別，必須先定義參考一個類別。

## <a name="syntax"></a>語法

```
/vmb
/vmg
```

## <a name="remarks"></a>備註

您也可以使用[pointers_to_members](../../preprocessor/pointers-to-members.md)或是[繼承關鍵字](../../cpp/inheritance-keywords.md)在您的程式碼，以指定的指標表示法。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
