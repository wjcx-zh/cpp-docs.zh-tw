---
title: 輔助線設定對話方塊 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLUs (dialog units)
- Dialog Editor [C++], snap to guides
- grid spacing
- guides, settings
- dialog units (DLUs)
- layout grid in Dialog Editor
- snap to guides (Dialog editor)
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
ms.assetid: 55381e1c-146a-4fa7-b1b3-b1492817615f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7369fdb37dbef474dafea2ba2a9a7e28f5eface9
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318885"
---
# <a name="guide-settings-dialog-box-c"></a>輔助線設定對話方塊 （c + +）

## <a name="layout-guides"></a>版面配置輔助線

顯示版面配置輔助線設定。

### <a name="none"></a>無

隱藏配置工具。

### <a name="rulers-and-guides"></a>尺規和輔助線

啟用時，加入尺規版面配置工具;指南可置於尺規。 預設指南是邊界，也可以藉由拖曳移動。 按一下尺規置放指南中。 控制 「 貼齊 」 指南上方或旁邊移動控制項時。 控制項也會一起移動指南之後，它們會附加至它。 當控制項所附加至每一端的指南，並移動輔助線時，會調整控制項的大小。

### <a name="grid"></a>Grid

建立版面配置方格。 新的控制項將自動貼齊格線。

## <a name="grid-spacing"></a>格線間距

對話方塊單位 (Dlu) 中，會顯示格線間距的設定。

### <a name="width-dlus"></a>寬度： Dlu

Dlu 中設定版面配置方格的寬度。 水平 DLU 是除以四對話方塊字型的平均寬度。

### <a name="height-dlus"></a>高度： Dlu

Dlu 中設定版面配置方格的高度。 垂直 DLU 是平均除以八個對話方塊字型的高度。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[修改配置格線](../windows/modifying-the-layout-grid.md)  
[對話方塊編輯器狀態 (輔助線和格線)](../windows/dialog-editor-states-guides-and-grids.md)