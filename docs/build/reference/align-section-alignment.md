---
title: /ALIGN （區段記憶體對齊） |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
dev_langs:
- C++
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb92d4b16be7903004831ffb25e2891f498a8989
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718246"
---
# <a name="align-section-alignment"></a>/ALIGN (區段對齊)

## <a name="syntax"></a>語法

> **/ALIGN**[**:**_數目_]

### <a name="arguments"></a>引數

*數字*<br/>
對齊值，以位元組為單位。

## <a name="remarks"></a>備註

**/對齊**選項會指定程式線性位址空間中的每個區段的對齊方式。 *數字*引數是以位元組為單位，而且必須是 2 的乘冪。 預設為 4k (4096)。 如果對齊方式會產生無效的映像，則連結器會發出警告。

除非您正在撰寫的應用程式，例如裝置驅動程式，您應該不需要修改對齊方式。

您可修改與對齊參數，以特定區段的對齊[/section](../../build/reference/section-specify-section-attributes.md)選項。

您指定的對齊值不得小於最大的區段記憶體對齊。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選擇**組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入中的選項**其他選項** 方塊中。 選擇 **[確定]** 或是**套用**以套用變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
