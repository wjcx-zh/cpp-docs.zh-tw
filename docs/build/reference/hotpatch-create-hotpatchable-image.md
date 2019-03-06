---
title: /hotpatch (建立可線上修補的影像)
ms.date: 11/12/2018
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
ms.openlocfilehash: aca009b108eab8a9e7e9401aa14db4ab225d475a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417849"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (建立可線上修補的影像)

準備映像進行 Hotpatch。

## <a name="syntax"></a>語法

```
/hotpatch
```

## <a name="remarks"></a>備註

當 **/hotpatch**用在編譯中，編譯器會確保每個函式的第一個指令會在至少兩個位元組，這是 hotpatch 所需要。

若要準備進行映像可進行 hotpatch，在使用後 **/hotpatch**進行編譯，您必須使用[/FUNCTIONPADMIN （建立可線上修補的影像）](../../build/reference/functionpadmin-create-hotpatchable-image.md)連結。 當您編譯和連結映像使用 cl.exe，一個引動過程 **/hotpatch**意味著 **/functionpadmin**。

因為指令永遠是兩個位元組或更大的 ARM 架構，而且因為 x64 編譯永遠會被視為如同 **/hotpatch**已指定，您不必指定 **/hotpatch**時在您針對這些目標; 編譯不過，您必須仍使用連結 **/functionpadmin**若要為其建立可線上修補的映像。 **/Hotpatch**編譯器選項只會影響 x86 編譯。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取  **C/c + +** 資料夾。

1. 選取 **命令列**屬性頁。

1. 加入至編譯器選項**其他選項** 方塊中。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
