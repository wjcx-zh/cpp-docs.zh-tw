---
title: 調整影像大小 (圖示影像編輯器)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
ms.openlocfilehash: d88a4cccff5b9b7b6303329782b7367cb953b13d
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484964"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>調整影像大小 (圖示影像編輯器)

行為**映像**編輯器時調整影像大小取決於您是否曾[選](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)只是部分或整個影像。

選取範圍包含只有部分映像，當**映像**編輯器會藉由刪除資料列或資料行的像素為單位，並以目前的背景色彩填滿空出的區域來縮小選取範圍。 它也可以複製資料列或資料行的像素為單位，以延伸選取範圍。

當選取範圍包含整個映像**映像**編輯器是壓縮和映像，會自動縮放或裁剪，並將它擴充。

有兩種機制來調整影像大小： 調整大小控點並[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您拖曳調整大小控點，若要變更的所有大小或影像的一部分。 您可以拖曳調整大小控點是純色。 您無法將拖曳空心的控制代碼。 使用**屬性**視窗重新調整整個影像，未選取的組件。

![縮放控點上的點陣圖](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
縮放控點

> [!NOTE]
> 如果您有**圖格的格線**中選取選項[格線設定對話方塊](../windows/grid-settings-dialog-box-image-editor-for-icons.md)，然後調整大小貼齊至下一個並排顯示格線。 如果只有**像素格線**選項是選取 （預設值），調整大小貼齊至下一個可用的像素。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="to-resize-an-entire-image-using-the-properties-window"></a>若要調整整個影像使用 [屬性] 視窗的大小

1. 開啟您想要變更其屬性的影像。

1. 在**寬度**並**高度**方塊[屬性 視窗](/visualstudio/ide/reference/properties-window)，輸入您想要的尺寸。

   如果您要增加的映像的大小**映像**編輯器擴充到右方時，向下、 影像或兩者，並使用目前的背景色彩填滿新的區域。 映像不會自動縮放。

   如果縮短映像的大小**映像**編輯器會裁剪的右邊緣或下邊緣，或兩者上的映像。

   > [!NOTE]
   > 您可以使用**寬度**並**高度**只整個調整影像大小，不是用來調整大小部分選取的屬性。

## <a name="to-crop-or-extend-an-entire-image"></a>若要裁剪或擴充整個影像

1. 選取整個影像。

   如果目前選取的映像的一部分，而且您想要選取整個影像，選取目前選取範圍框線外面的映像上的任何位置。

1. 拖曳調整大小控點，直到的影像是正確的大小。

通常**映像**裁切編輯器，或當您調整所移動的縮放控點，放大影像。 如果您按住**Shift**鍵移動的縮放控點，**映像**編輯器縮小或延伸影像。

## <a name="to-shrink-or-stretch-an-entire-image"></a>若要縮小或延伸整個影像

1. 選取整個影像。

   如果目前選取的映像的一部分，而且您想要選取整個影像，選取目前選取範圍框線外面的映像上的任何位置。

1. 按住**Shift**鍵並拖曳調整大小控點，直到映像的正確大小。

## <a name="to-shrink-or-stretch-part-of-an-image"></a>若要縮小或拉長影像的一部分

1. 選取您想要調整大小的映像的一部分。 如需詳細資訊，請參閱 <<c0> [ 選取影像的區域](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)。

1. 拖曳調整大小控點，直到選取範圍是正確的大小。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[圖示影像編輯器](../windows/image-editor-for-icons.md)