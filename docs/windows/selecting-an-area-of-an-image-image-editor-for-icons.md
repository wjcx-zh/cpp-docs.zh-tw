---
title: 選取影像的範圍 (圖示影像編輯器)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
ms.openlocfilehash: 5e2522d23b30a91639e887a8761871e3df8139f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565109"
---
# <a name="selecting-an-area-of-an-image-image-editor-for-icons"></a>選取影像的範圍 (圖示影像編輯器)

您可以使用 選取工具來定義您想要剪下、 複製、 清除、 調整大小、 反轉，或移動之影像的區域。 具有**矩形選取範圍**工具，您可以定義，並選取影像的矩形區域。 具有**不規則的選取項目**工具，您可以繪製徒手畫的外框範圍，您想要選取剪下、 複製或其他作業。

> [!NOTE]
> 請參閱**矩形選取範圍**並**不規則的選取項目**工具所示[影像編輯器工具列](../windows/toolbar-image-editor-for-icons.md)或檢視上每個按鈕相關聯的工具提示**影像編輯器**工具列。

您也可以從選取項目建立自訂筆刷。 如需詳細資訊，請參閱 <<c0> [ 建立自訂筆刷](../windows/creating-a-custom-brush-image-editor-for-icons.md)。

### <a name="to-select-an-area-of-an-image"></a>若要選取的映像區域

1. 上**影像編輯器**工具列 (或從**映像**功能表**工具**命令)，按一下您要的選取範圍工具。

2. 將插入點移至您想要選取的影像區域的其中一個角落。 出現十字型游標停留在影像上時。

3. 將插入點拖曳到相反邊角，您想要選取的區域中。 矩形會顯示將選取的像素為單位。 在矩形中，包括矩形下方的所有像素會包含在選取項目。

4. 放開滑鼠按鈕。 選取框線包圍選取的區域。

### <a name="to-select-an-entire-image"></a>若要選取整個影像

1. 按一下目前的選取範圍外的影像。 選取框線焦點變更，並再次包含整個影像。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[圖示影像編輯器](../windows/image-editor-for-icons.md)