---
title: -bigobj （增加中的區段數目。Obj 檔） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /bigobj
dev_langs:
- C++
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f10456bea8be552df42efe135818ac9c47393fc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721483"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (增加 .Obj 檔中的區段數目)

**/bigobj**會增加物件檔案可以包含的區段數目。

## <a name="syntax"></a>語法

```
/bigobj
```

## <a name="remarks"></a>備註

根據預設，物件檔案可以保留最多 65,536 (2 ^16) 可定址區段。 無論指定哪個目標平台，都會發生這種情況。 **/bigobj**增加 4294967296 該位址容量 (2 ^32)。

大部分的模組絕不會產生的.obj 檔案，包含超過 65536 的區段。 不過，機器產生的程式碼，或大量使用的範本程式庫的程式碼可能需要可以保存多個區段的.obj 檔案。 **/bigobj**因為機器產生的 XAML 程式碼包含大量標頭的通用 Windows 平台 (UWP) 專案的預設會啟用。 如果您停用此選項在 UWP 應用程式專案您可能會發生編譯器錯誤 C1128。

隨附在 Visual c + + 2005年之前的連結器無法讀取與所產生的.obj 檔案 **/bigobj**。

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