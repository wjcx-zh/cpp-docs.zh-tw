---
title: 對齊控制項
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
ms.assetid: a4f49a73-4a17-44b3-8568-aa35f646b5cf
ms.openlocfilehash: abfae0f0146fa736a6427eb1180805717ce8a78e
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484977"
---
# <a name="align-controls"></a>對齊控制項

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

下列程序會示範如何將控制項對齊：

## <a name="to-align-groups-of-controls"></a>若要對齊控制項群組

1. [選取的控制項](../windows/selecting-multiple-controls.md)您想要對齊。 請務必選取您想要先做為主控制項的控制項或將它設為執行對齊或調整大小命令之前的主要控制項。

   控制項群組的最後一個位置是根據主控制項的位置而定。 如需有關選取主控項的詳細資訊，請參閱[指定主控項](../windows/specifying-the-dominant-control.md)。

1. 從**格式**功能表上，選擇**對齊**，然後選擇下列的對齊方式的其中一個：

   - `Lefts`： 將選取的控制項，沿著左邊對齊。

   - `Centers`： 將選取的控制項，沿著中心點的水平對齊。

   - `Rights`： 將選取的控制項，沿著右邊對齊。

   - `Tops`： 將選取的控制項，沿著上邊緣對齊。

   - `Middles`： 將選取的控制項，沿著垂直中間點對齊。

   - `Bottoms`： 將選取的控制項，沿著下邊緣對齊。

## <a name="to-even-the-spacing-between-controls"></a>若要均等控制項之間的間距

** 對話方塊**編輯器可讓您選取的最外層的控制項之間的平均空間控制項。

1. 選取您想要重新排列的控制項。

1. 從**格式**功能表上，選擇**均等空格**，然後選擇下列間距對齊方式的其中一個：

   - `Across`： 空間平均之間最左邊和右邊的控制項選取的控制項。

   - `Down`： 空間平均之間的最上層和選取的最下層控制項的控制項。

## <a name="to-center-controls-in-a-dialog-box"></a>若要在對話方塊中的控制項置中

1. 選取您想要重新排列的控制項。

1. 從**格式**功能表上，選擇**對齊對話方塊中央**，然後選擇下列的排列方式的其中一個：

   - `Vertical`： 控制項在對話方塊中，垂直置中。

   - `Horizontal`： 控制項在對話方塊中的水平置中。

## <a name="to-arrange-push-buttons-along-the-right-or-bottom-of-a-dialog-box"></a>若要沿著右側或對話方塊的底部排列按鈕

1. 選取一或多個按鈕。

1. 從**格式**功能表上，選擇**排列按鈕**，然後選擇下列的排列方式的其中一個：

   - `Right`： 沿著對話方塊的右邊緣對齊按鈕。

   - `Bottom`： 對齊按鈕的對話方塊中的下邊緣。

       如果您選取按鈕以外的控制項，其位置不受影響。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊上控制項的排列方式](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[控制項](../mfc/controls-mfc.md)