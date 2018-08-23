---
title: 建立及設定輔助線和邊界 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- guides, clearing
- guides
- Dialog editor, guides and margins
- dialog box controls, placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
ms.assetid: fafa4545-8f00-436f-b590-300e76601156
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2fedae08467243c0fe981b287e63f4e2e041d910
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589162"
---
# <a name="creating-and-setting-guides-and-margins"></a>建立、設定輔助線和邊界

無論您要移動控制項，加入控制項，或重新排列目前的配置，指南可以幫助您對齊正確的對話方塊內的控制項。 指南會以藍色的虛線顯示在 [顯示在編輯器和對應的箭號，在 [尺規] 對話方塊中 (在頂端，並沿著左側 **] 對話方塊**編輯器)。

當您建立對話方塊中時，會提供四個邊界。 邊界是修改過的指南，顯示為藍色的虛線。

### <a name="to-create-a-guide"></a>若要建立的指南

1. 中的尺規，請按一次可建立的指南。 (按一下建立新指南; 按兩下 launch[輔助線設定對話方塊](../windows/guide-settings-dialog-box.md)，您可以在其中指定輔助線設定。)

### <a name="to-set-a-guide"></a>若要設定指南

1. 在對話方塊中，按一下快速入門，並將它拖曳到新位置。 （您也可以按一下尺規，即可將相關聯的指南中的箭號）。

   本指南的座標會顯示在視窗底部的狀態列和尺規中的區段。 您可以將指標移到尺規，以顯示快速入門的確切位置中的箭號。

### <a name="to-delete-a-guide"></a>若要刪除輔助線

1. 輔助線拖曳立即可用的對話方塊。

\-或-

- 拖曳對應的箭號，離開尺規。

### <a name="to-move-margins"></a>若要移動邊界

1. 拖曳到新位置的邊界。

   若要讓邊界消失，將邊界移到零的位置。 若要恢復邊界，將指標放置於邊界的零位置，將邊界移至的位置。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊編輯器狀態 (輔助線和格線)](../windows/dialog-editor-states-guides-and-grids.md)  
[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)