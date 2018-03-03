---
title: "對齊輔助線上的控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eed9acf533939d305e42478bb87307bc0a055d3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="aligning-controls-on-a-guide"></a>對齊輔助線上的控制項
控制項的調整大小控點貼齊輔助線時移動控制項，以及控制項貼齊輔助線 （如果不有任何控制項先前貼齊輔助線）。 當移動時的指南時，以及移動會貼齊至它的控制項。 其中一個指南移動時，會調整大小控制項貼齊至一個以上的指南。  
  
 對話方塊單位 (Dlu) 定義決定輔助線和控制項的間距尺規中的刻度標記。 DLU 根據對話方塊字型，通常 8 點 MS Shell Dlg 的大小。 水平 DLU 是由四個分割對話方塊字型的平均寬度。 垂直 DLU 是平均除以八個字型的高度。  
  
### <a name="to-size-a-group-of-controls-with-guides"></a>若要控制項群組的大小與指南  
  
1.  貼齊輔助線 （或多個控制項） 的一端。  
  
2.  拖曳的控制項 （或控制項） 的另一端的指南。  
  
     視需要使用多個控制項，調整大小以第二個指南貼齊。  
  
3.  移動其中一個指南控制項 （或控制項） 的大小。  
  
### <a name="to-change-the-intervals-of-the-tick-marks"></a>若要變更的刻度標記間隔  
  
1.  從**格式**功能表上，選擇**輔助線設定**。  
  
2.  在[輔助線設定對話方塊](../windows/guide-settings-dialog-box.md)，請在**格線間距**欄位中指定 Dlu 新寬度和高度。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 需求  
  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [對話方塊編輯器狀態 （輔助線和格線）](../windows/dialog-editor-states-guides-and-grids.md)   
 [對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)

