---
title: 對齊控制項群組 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], aligning
ms.assetid: a4f49a73-4a17-44b3-8568-aa35f646b5cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c791f2951eb7ac9947d48b563bde624bc3b7979f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393577"
---
# <a name="aligning-groups-of-controls"></a>對齊控制項群組

下列程序會示範如何對齊控制項群組。

### <a name="to-align-groups-of-controls"></a>若要對齊控制項群組

1. [選取的控制項](../windows/selecting-multiple-controls.md)您想要對齊。 請務必選取您想要先做為主控制項的控制項或將它設為執行對齊或調整大小命令之前的主要控制項。

   控制項群組的最後一個位置是根據主控制項的位置而定。 如需有關選取主控項的詳細資訊，請參閱[指定主控項](../windows/specifying-the-dominant-control.md)。

2. 從**格式**功能表上，選擇**對齊**，然後選擇下列的對齊方式的其中一個：

   - `Lefts`： 將選取的控制項，沿著左邊對齊。

   - `Centers`： 將選取的控制項，沿著中心點的水平對齊。

   - `Rights`： 將選取的控制項，沿著右邊對齊。

   - `Tops`： 將選取的控制項，沿著上邊緣對齊。

   - `Middles`： 將選取的控制項，沿著垂直中間點對齊。

   - `Bottoms`： 將選取的控制項，沿著下邊緣對齊。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊上控制項的排列方式](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[控制項](../mfc/controls-mfc.md)