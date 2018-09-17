---
title: -vmb、-vmg （表示方法） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vmb
- /vmg
dev_langs:
- C++
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a95081dfb417711002039727b04d1916c5fe0a14
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720573"
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

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)