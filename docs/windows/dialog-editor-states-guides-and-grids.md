---
title: 對話方塊編輯器狀態 （輔助線和格線） （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], guides and margins
- guides, clearing
- guides
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
- guides, disabling snapping
- controls [C++], snap to guides/grid
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
- grid spacing
- guides, settings
- layout grid in Dialog Editor
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
ms.assetid: dbacf9ef-e8b0-4125-a7ce-84911c482e98
ms.openlocfilehash: 52fc19d8a39680c16692177e2758fba78afc7d3a
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484990"
---
# <a name="dialog-editor-states-guides-and-grids-c"></a>對話方塊編輯器狀態 （輔助線和格線） （c + +）

您可以使用對話方塊上的控制項排列 **對話方塊**編輯器中的三個不同的狀態：

- 使用輔助線和邊界的 （預設值）

- 上的配置格線

- 不需要任何貼齊 」 或 「 對齊 」 功能

[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)包含控制項狀態的按鈕。 若要變更狀態，按一下適當的圖示。 您也可以藉由變更狀態**輔助線設定**命令**格式**功能表。

**輔助線設定**對話方塊具有下列屬性：

|屬性|描述|
|---|---|
|**版面配置輔助線**|顯示版面配置輔助線設定。|
|**無**|隱藏配置工具。|
|**尺規和輔助線**|啟用時，加入尺規版面配置工具;指南可置於尺規。 預設指南是邊界，也可以藉由拖曳移動。 選取要放置指南尺規。 控制 「 貼齊 」 指南上方或旁邊移動控制項時。 控制項也會一起移動指南之後，它們會附加到它。 當控制項所附加至每一端的指南，並移動輔助線時，控制項會調整大小。|
|**格線**|建立版面配置方格。 新的控制項將自動貼齊格線。|
|**格線間距**|對話方塊單位 (Dlu) 中，會顯示格線間距的設定。|
|**Width:Dlu**|Dlu 中設定版面配置方格的寬度。 水平 DLU 是除以四對話方塊字型的平均寬度。|
|**Height:Dlu**|Dlu 中設定版面配置方格的高度。 垂直 DLU 是平均除以八個對話方塊字型的高度。|

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="create-and-set-guides-and-margins"></a>建立並設定輔助線和邊界

無論您要移動控制項，加入控制項，或重新排列目前的版面配置輔助線可以幫助您對齊正確的對話方塊內的控制項。 指南會以藍色的虛線顯示跨對應尺規上方，並沿著左側的箭號與編輯器中顯示的對話方塊** 對話方塊**編輯器。

當您建立對話方塊中時，會提供四個邊界。 邊界是修改過的指南，顯示為藍色的虛線。

### <a name="to-create-a-guide"></a>若要建立的指南

中的尺規，請按一次可建立的指南。 (按一下建立新指南; 按兩下 launch**輔助線設定**對話方塊中，您可以在其中指定輔助線設定。)

### <a name="to-set-a-guide"></a>若要設定指南

在對話方塊中，按一下快速入門，並將它拖曳到新位置。 （您也可以按一下尺規，即可將相關聯的指南中的箭號）。

本指南的座標會顯示在視窗底部的狀態列和尺規中的區段。 您可以將指標移到尺規，以顯示快速入門的確切位置中的箭號。

### <a name="to-delete-a-guide"></a>若要刪除輔助線

輔助線拖曳立即可用的對話方塊。

\-或-

拖曳對應的箭號，離開尺規。

### <a name="to-move-margins"></a>若要移動邊界

拖曳到新位置的邊界。

若要讓邊界消失，將邊界移到零的位置。 若要回復邊界，將指標放置於邊界的零位置，將邊界移到位置。

## <a name="align-controls-on-a-guide"></a>對齊輔助線上的控制項

當控制項不會移動，並輔助線嵌入式管理單元至控制項，如果不有任何先前貼齊輔助線的控制項，控制項的調整大小控點就貼齊格線。 當移動時的指南時，會貼齊至它的控制項就會一併移動。 當其中一個指南移動，則會調整大小貼齊至一個或多個指南的控制項。

對話方塊單位 (Dlu) 會定義中判斷的間距輔助線和控制項的尺規的刻度標記。 DLU 根據對話方塊字型，通常 8-point MS Shell Dlg 的大小。 水平 DLU 是除以四對話方塊字型的平均寬度。 垂直 DLU 是平均除以八字型的高度。

### <a name="to-size-a-group-of-controls-with-guides"></a>若要有輔助線大小的控制項群組

1. 貼齊輔助線 （或多個控制項） 的一端。

1. 拖曳的控制項 （或控制項） 的另一端的指南。

   視需要使用多個控制項，調整大小，每個貼齊至第二個指南。

1. 移動至控制項 （或控制項） 的大小是輔助線。

### <a name="to-change-the-intervals-of-the-tick-marks"></a>若要變更刻度的間隔

1. 從**格式**功能表上，選擇**輔助線設定**。

1. 在 **輔助線設定**對話方塊中，於**格線間距**欄位中，指定新的寬度和高度 Dlu 中。

## <a name="disable-guides"></a>停用輔助線

若要停用的貼齊輔助線效果，您可以搭配滑鼠使用特殊的索引鍵。 使用**Alt**金鑰會停用的貼齊選取快速入門的效果。 移動有的快速入門**Shift**金鑰可防止貼齊的控制項移動與指南。

### <a name="to-disable-the-snapping-effect-of-the-guides"></a>若要停用的貼齊輔助線效果

將控制項拖曳時按住**Alt**索引鍵。

### <a name="to-move-guides-without-moving-the-snapped-controls"></a>若要移動輔助線，而不移動貼齊的控制項

輔助線拖曳時按住**Shift**索引鍵。

### <a name="to-turn-off-the-guides"></a>若要關閉指南

1. 從**格式**功能表上，選擇**輔助線設定**。

1. 在 **輔助線設定**對話方塊的 **版面配置輔助線**，選取**None**。

   > [!NOTE]
   > 您也可以按兩下 尺規 列，來存取**輔助線設定** 對話方塊。

\-或-

在 **格式**功能表上，選取**切換輔助線**。

## <a name="modify-the-layout-grid"></a>修改配置格線

當您放置或在對話方塊中排列控制項時，您可以使用版面配置方格的更精確的位置。 方格開啟時，控制項便會出現 「 貼齊 」 方格的虛線如同 magnetized。 您可以開啟和關閉此 「 貼齊至格線 」 功能，並變更版面配置方格資料格的大小。

### <a name="to-turn-the-layout-grid-on-or-off"></a>若要開啟或關閉的版面配置方格

1. 從**格式**功能表上，選擇**輔助線設定**。

1. 在 **輔助線設定** 對話方塊中，選取或清除**格線** 按鈕。

   您仍可控制中個別的方格** 對話方塊**使用的編輯器視窗**切換格線**按鈕[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

### <a name="to-change-the-size-of-the-layout-grid"></a>若要變更版面配置方格的大小

1. 從**格式**功能表上，選擇**輔助線設定**。

1. 在 **輔助線設定**對話方塊方塊中，輸入的高度和寬度 Dlu 針對方格中的資料格。 最小高度或寬度是 4 Dlu。 如需有關 Dlu 的詳細資訊，請參閱[排列方式的對話方塊上控制項](../windows/arrangement-of-controls-on-dialog-boxes.md)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[控制項 (MFC)](../mfc/controls-mfc.md)<br/>
