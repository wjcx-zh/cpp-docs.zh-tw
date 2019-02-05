---
title: 調整控制項的大小
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.combo
helpviewer_keywords:
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
ms.openlocfilehash: a6381dcf1aeb9f73ac3b656229d9332df2a6a519
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742709"
---
# <a name="sizing-controls"></a>調整控制項的大小

您可以使用調整大小控點來調整控制項大小。 當指標位於其上的縮放控點時，它會變更形狀，以表示控制項可以在其中調整大小的指示。 作用中的縮放控點是純色;如果空心的縮放控點，則無法調整大小控制該軸。

您也可以藉由貼齊輔助線或邊界，以控制變更控制項大小或移動其中一個貼齊控制項和輔助線與另一個。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="to-size-an-individual-control"></a>若要個別控制項的大小

1. 選取的控制項。

1. 拖曳調整大小控點，若要變更控制項的大小：

   - 在頂端和側邊的調整大小控點會變更水平或垂直大小。

   - 邊角調整大小控點會變更水平和垂直大小。

   > [!TIP]
   > 一次調整控制項的一個對話方塊單位 (DLU) 大小按住**Shift**鍵並使用**向右箭號**並**向下箭號**索引鍵。

## <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>若要自動調整大小以容納內文字的控制項

選擇**內容的大小**從**格式**功能表。

\-或-

以滑鼠右鍵按一下控制項，然後選擇 **內容的大小**從捷徑功能表。

## <a name="to-make-controls-the-same-width-height-or-size"></a>若要讓控制項相同的寬度、 高度或大小

您可以調整大小一的組控制項以主控項的大小。

1. [選取的控制項](../windows/selecting-multiple-controls.md)您想要調整大小。

   第一次選取數列中的控制項是主要的控制項。 群組中控制項的最終大小取決於主控制項的大小。 如需有關選取主控項的詳細資訊，請參閱[指定主控](../windows/specifying-the-dominant-control.md)。

1. 從**格式**功能表上，選擇**成相同大小**，然後選擇其中一個下列命令：

   - **兩者**

   - [高度]

   - [寬度]

## <a name="to-set-the-size-of-the-combo-box-and-its-drop-down-list"></a>若要設定大小的下拉式方塊和下拉式清單

當您將它新增至對話方塊中，您可以調整大小的下拉式方塊。 您也可以指定下拉式清單方塊的大小。 如需詳細資訊，請參閱 <<c0> [ 新增至下拉式方塊控制項的值](../windows/adding-values-to-a-combo-box-control.md)。

### <a name="to-size-a-combo-box"></a>若要調整大小的下拉式方塊

1. 在您的對話方塊中，選取下拉式方塊控制項。

   一開始僅左邊和右邊的調整大小控點會有作用中。

1. 您可以使用調整大小控點來設定下拉式方塊的寬度。

您也可以設定下拉式方塊的下拉式部分的垂直大小。

### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>若要設定大小的下拉式方塊的下拉式清單

1. 選取右邊的下拉式方塊的下拉箭號按鈕。

   ![在 MFC 專案下拉式方塊上的箭號](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   控制變更，以顯示下拉式方塊的大小與擴充的下拉式清單中區域的外框。

1. 您可以使用較低的調整大小控點，變更下拉式清單 區域的初始大小。

   ![下拉式方塊&#45;MFC 專案中的方塊縮放](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. 選取下拉式箭號，以關閉下拉式方塊的下拉式清單部分。

## <a name="to-set-the-width-of-a-horizontal-scroll-bar-and-make-it-appear"></a>設定水平捲軸的寬度，並讓它出現

當您使用 MFC 類別的對話方塊中新增具有水平捲軸的清單方塊時，捲軸不會自動出現在您的應用程式。

藉由呼叫設定的最寬的項目最大寬度[CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent)程式碼中。

   沒有設定這個值，捲軸不會出現，即使當清單方塊中的項目都超出 方塊中。
> [!NOTE]
> 水平捲軸需要 MFC。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[控制項](../mfc/controls-mfc.md)
