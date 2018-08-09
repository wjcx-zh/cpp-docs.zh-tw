---
title: 對齊輔助線上的控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLUs (dialog units)
- controls [C++], aligning
- Dialog editor, snap to guides
- guides, tick mark interval
- dialog box controls, placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
ms.assetid: 17db84ba-5288-4478-be57-afa748aa6447
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a1a586a3a17e829d883dff96c12f6a2fdabe669f
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643854"
---
# <a name="aligning-controls-on-a-guide"></a>對齊輔助線上的控制項
當控制項不會移動，且控制項貼齊輔助線 （如果不有任何先前貼齊輔助線的控制項） 時，控制項的調整大小控點就貼齊格線。 當移動時的指南時，會貼齊至它的控制項就會一併移動。 當其中一個指南移動，則會調整大小貼齊至一個或多個指南的控制項。  
  
 對話方塊單位 (Dlu) 會定義中判斷的間距輔助線和控制項的尺規的刻度標記。 DLU 根據對話方塊字型，通常 8-point MS Shell Dlg 的大小。 水平 DLU 是除以四對話方塊字型的平均寬度。 垂直 DLU 是平均除以八字型的高度。  
  
### <a name="to-size-a-group-of-controls-with-guides"></a>若要有輔助線大小的控制項群組  
  
1.  貼齊輔助線 （或多個控制項） 的一端。  
  
2.  拖曳的控制項 （或控制項） 的另一端的指南。  
  
     視需要使用多個控制項，調整大小，每個貼齊至第二個指南。  
  
3.  移動至控制項 （或控制項） 的大小是輔助線。  
  
### <a name="to-change-the-intervals-of-the-tick-marks"></a>若要變更刻度的間隔  
  
1.  從**格式**功能表上，選擇**輔助線設定**。  
  
2.  在 [輔助線設定對話方塊](../windows/guide-settings-dialog-box.md)，請在**格線間距**欄位中，指定在 Dlu 中的新寬度和高度。  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊編輯器狀態 （輔助線和格線）](../windows/dialog-editor-states-guides-and-grids.md)   
 [對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)