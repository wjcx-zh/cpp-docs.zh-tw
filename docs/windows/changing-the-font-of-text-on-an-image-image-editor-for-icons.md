---
title: 將影像 （圖示影像編輯器） 上的文字字型變更 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- fonts, changing on an image
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0898d8a787c6d2c14f341a31e202738d666cdf86
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678460"
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>變更影像上的文字字型 (圖示影像編輯器)

下列程序是如何的範例：

- 將文字新增至 Windows 應用程式中的圖示

- 管理您的文字的字型

### <a name="to-change-the-font-of-text-on-an-image"></a>若要變更的映像上的文字的字型

1. 建立 c + + Windows Forms 應用程式。 如需詳細資訊，請參閱 <<c0> [ 建立 Windows 應用程式專案](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5\(v=vs.100\))。 `app.ico`檔案預設會新增至您的專案。

2. 在 [**方案總管] 中**，連按兩下檔案 app.ico。 [影像編輯器](../windows/image-editor-for-icons.md)隨即開啟。

3. 從**映像**功能表上，選取**工具**，然後選取**文字工具**。 [文字工具對話方塊](../windows/text-tool-dialog-box-image-editor-for-icons.md)會出現。

4. 在 [**文字工具**] 對話方塊中，輸入`C++`空的文字區域中。 此文字會出現在可調整大小的方塊的左角`app.ico`，請在**影像編輯器**。

5. 在 **影像編輯器**，將可調整大小的方塊拖曳到 app.ico 中心，以改善文字的可讀性。

6. 在 **文字工具** 對話方塊中，按一下**字型** 按鈕。 [文字工具字型對話方塊](../windows/text-tool-font-dialog-box-image-editor-for-icons.md)會出現。

7. 在 **文字工具字型**對話方塊中，選取**Times New Roman**從清單中所列的可用字型**字型**清單方塊。

8. 選取 **粗體**從清單中列出可用的字型樣式**字型樣式**清單方塊。

9. 選取  **10**從可用的點中所列的大小**大小**清單方塊。

10. 按一下 [**確定**] 按鈕。 **文字工具字型**對話方塊會關閉，而新的字型設定將套用到您的文字。

11. 按一下 [**關閉**按鈕**文字工具**] 對話方塊。 可調整您在文字周圍方塊會從消失**影像編輯器**。

## <a name="see-also"></a>另請參閱

[編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[工具列](../windows/toolbar-image-editor-for-icons.md)