---
title: "/ALIGN （區段對齊） |Microsoft 文件"
ms.custom: 
ms.date: 12/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
dev_langs: C++
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ca4572e84c7ad32be2d03a312f7bb7d8a3f3f29
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="align-section-alignment"></a>/ALIGN (區段對齊)

## <a name="syntax"></a>語法

> **/ALIGN**[**:**_數目_]

### <a name="arguments"></a>引數

*數字*  
對齊值，以位元組為單位。

## <a name="remarks"></a>備註

**/對齊**選項會指定程式的線性位址空間中的每個區段的對齊方式。 *數目*引數是以位元組為單位，且必須是 2 的乘冪。 預設值是 4 K (4096)。 連結器會發出警告，就會產生無效的影像對齊方式。

除非您正在撰寫的應用程式，例如裝置驅動程式，您應該不需要修改對齊方式。

可修改的特定區段的對齊參數與對齊[/section](../../build/reference/section-specify-section-attributes.md)選項。

您指定的對齊值不得小於最大區段記憶體對齊。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選擇**組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入中的選項**其他選項**方塊。 選擇**確定**或**套用**以套用變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)  
[連結器選項](../../build/reference/linker-options.md)  
