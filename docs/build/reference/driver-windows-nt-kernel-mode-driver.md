---
title: -驅動程式 （Windows NT 核心模式驅動程式） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ae096c502cdc94d47a516caf4c29ac4f3eceb4b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705545"
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER (Windows NT 核心模式驅動程式)

>/ 驅動程式 [: UPONLY |: WDM]

## <a name="remarks"></a>備註

使用 **/DRIVER**連結器選項，來建置 Windows NT 核心模式驅動程式。

**/Driver: uponly**會導致連結器將加入**IMAGE_FILE_UP_SYSTEM_ONLY**位元來指定它是單一處理器 (UP) 驅動程式的輸出標頭中的特性。 作業系統會拒絕將 UP 驅動程式的多處理器 (MP) 系統上。

**/Driver: wdm**使設定連結器**IMAGE_DLLCHARACTERISTICS_WDM_DRIVER**選擇性標頭的 DllCharacteristics 欄位中的位元。

如果 **/DRIVER**未指定，連結器未設定這些位元。

如果 **/DRIVER**指定：

- **/Fixed: no**作用中。 如需詳細資訊，請參閱 [/FIXED (固定基底位址)](../../build/reference/fixed-fixed-base-address.md)。

- 輸出檔的副檔名設為.sys。 使用 **/out**若要變更的預設檔名和副檔名。 如需詳細資訊，請參閱 [/OUT (輸出檔名稱)](../../build/reference/out-output-file-name.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **系統**屬性頁。

1. 修改**驅動程式**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱[VCLinkerTool.driver 屬性](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver?view=visualstudiosdk-2017#Microsoft_VisualStudio_VCProjectEngine_VCLinkerTool_driver)。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
