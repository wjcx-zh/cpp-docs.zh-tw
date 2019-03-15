---
title: /ALIGN (區段對齊)
ms.date: 12/29/2017
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
ms.openlocfilehash: d8d2e6a859c68af473d49dc04b76f0a15056aa56
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "57809466"
---
# <a name="align-section-alignment"></a>/ALIGN (區段對齊)

## <a name="syntax"></a>語法

> **/ALIGN**[**:**_數目_]

### <a name="arguments"></a>引數

*number*<br/>
對齊值，以位元組為單位。

## <a name="remarks"></a>備註

**/對齊**選項會指定程式線性位址空間中的每個區段的對齊方式。 *數字*引數是以位元組為單位，而且必須是 2 的乘冪。 預設為 4k (4096)。 如果對齊方式會產生無效的映像，則連結器會發出警告。

除非您正在撰寫的應用程式，例如裝置驅動程式，您應該不需要修改對齊方式。

您可修改與對齊參數，以特定區段的對齊[/section](section-specify-section-attributes.md)選項。

您指定的對齊值不得小於最大的區段記憶體對齊。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選擇**組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入中的選項**其他選項** 方塊中。 選擇 **[確定]** 或是**套用**以套用變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
