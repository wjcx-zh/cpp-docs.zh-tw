---
title: "驅動程式 （Windows NT 核心模式驅動程式） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
dev_langs:
- C++
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29234e3c0e368c7710f9071c753422bc4e6ef2b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER (Windows NT 核心模式驅動程式)

>/ 驅動程式 [: UPONLY |: WDM]

## <a name="remarks"></a>備註

使用**/DRIVER**連結器選項，來建置 Windows NT 核心模式驅動程式。

**/Driver: uponly**會使連結器將**IMAGE_FILE_UP_SYSTEM_ONLY**位元到輸出標頭，以指定它是單一處理器 (UP) 驅動程式中的特性。 作業系統會拒絕載入多處理器 (MP) 系統將 UP 驅動程式。

**/Driver: wdm**使連結器設定**IMAGE_DLLCHARACTERISTICS_WDM_DRIVER**選擇性標頭的 DllCharacteristics 欄位中的位元。

如果**/DRIVER**未指定，則依連結器將不會設定這些位元。

如果**/DRIVER**指定：

- **/Fixed: no**作用中。 如需詳細資訊，請參閱 [/FIXED (固定基底位址)](../../build/reference/fixed-fixed-base-address.md)。

- 輸出檔的副檔名設為.sys。 使用**/out**若要變更預設檔名和副檔名。 如需詳細資訊，請參閱 [/OUT (輸出檔名稱)](../../build/reference/out-output-file-name.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下**連結器**資料夾。

1. 按一下**系統**屬性頁。

1. 修改**驅動程式**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱[VCLinkerTool.driver 屬性](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver?view=visualstudiosdk-2017#Microsoft_VisualStudio_VCProjectEngine_VCLinkerTool_driver)。

## <a name="see-also"></a>請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)   
[連結器選項](../../build/reference/linker-options.md)
