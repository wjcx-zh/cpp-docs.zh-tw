---
title: /DRIVER (Windows NT 核心模式驅動程式)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
ms.openlocfilehash: 5639344ede4007bd66a3d51043f4acb423426b94
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842971"
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER (Windows NT 核心模式驅動程式)

>/DRIVER [： UPONLY |： WDM]

## <a name="remarks"></a>備註

使用 **/DRIVER** 連結器選項來建立 Windows NT 核心模式驅動程式。

**/DRIVER： UPONLY** 會讓連結器將 **IMAGE_FILE_UP_SYSTEM_ONLY** 位新增至輸出標頭中的特性，以指定它是) 驅動程式的單處理器 (。 作業系統會拒絕將驅動程式載入多處理器 (MP) 系統上。

**/DRIVER： WDM** 會導致連結器在選用標頭的 DLLCHARACTERISTICS 欄位中設定 **IMAGE_DLLCHARACTERISTICS_WDM_DRIVER** 位。

如果未指定 **/DRIVER** ，連結器就不會設定這些位。

如果指定了 **/DRIVER** ：

- **/FIXED：沒有** 作用中。 如需詳細資訊，請參閱 [/FIXED (固定基底位址)](fixed-fixed-base-address.md)。

- 輸出檔的副檔名設定為 sys。 使用 **/out** 來變更預設的檔案名和副檔名。 如需詳細資訊，請參閱 [/OUT (輸出檔名稱)](out-output-file-name.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **Linker** 資料夾。

1. 按一下 [ **系統** ] 屬性頁。

1. 修改 **驅動程式** 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 [VCLinkerTool. 驅動程式屬性](/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver?view=visualstudiosdk-2017#Microsoft_VisualStudio_VCProjectEngine_VCLinkerTool_driver)。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
