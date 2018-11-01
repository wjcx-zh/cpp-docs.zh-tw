---
title: 建立裝置影像 (圖示影像編輯器)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
helpviewer_keywords:
- cursors [C++], creating
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
ms.openlocfilehash: 322205e22edf2624784ddb8f294bcf5e73af06f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447747"
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>建立裝置影像 (圖示影像編輯器)

當您建立新的圖示或游標資源**映像**先在特定的樣式 （32 × 32，16 種色彩圖示和 32 × 32，資料指標的單色） 中建立映像的編輯器。 然後將映像不同大小和樣式加入初始的圖示或游標，並視需要編輯每個額外的映像，適用於不同的顯示裝置。 您也可以藉由執行剪下和貼上作業，從現有的映像類型，或從點陣圖圖形程式中建立編輯映像。

當您開啟中的圖示或游標資源[影像編輯器](../windows/image-editor-for-icons.md)，預設會開啟大部分十分符合目前的顯示裝置的映像。

### <a name="to-create-a-new-icon-or-cursor"></a>若要建立新的圖示或游標

1. 在 [資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下.rc 檔，然後選擇**插入資源**從捷徑功能表。 (如果您已經有現有的映像資源在.rc 檔案中，例如資料指標中，您可以直接以滑鼠右鍵按一下**游標**資料夾，然後選取**插入游標**從捷徑功能表。)

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 在[插入資源對話方塊](../windows/add-resource-dialog-box.md)，選取**圖示**或**游標**然後按一下**新增**。 圖示，這會使用 32 × 32、 16 色圖示建立圖示資源。 資料指標，32 × 32，會建立單色 （2-色彩） 映像。

   如果一個加號 (**+**) 中的映像資源類型旁邊會出現**插入資源** 對話方塊中，表示工具列範本可供使用。 按一下加號，展開 範本清單，選取範本，然後按一下**新增**。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[圖示和游標： 顯示裝置的影像資源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[圖示和游標： 顯示裝置的影像資源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)