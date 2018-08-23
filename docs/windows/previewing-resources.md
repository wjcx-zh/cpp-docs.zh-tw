---
title: 預覽資源 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- resource previews
- code, viewing
ms.assetid: d6abda66-0e2b-4ac3-a59a-a57b8c6fb70b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e6e15a4557d8368596021307ba7045bfb4b08664
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583828"
---
# <a name="previewing-resources"></a>預覽資源

預覽您的資源，可讓您檢視圖形化的資源，而不需要開啟它們。 預覽功能也適用於可執行檔的資源識別元變更為 數字，因為編譯它們後。 通常這些數值識別項未提供足夠的資訊，因為預覽的資源可協助您快速找出它們。

您可以預覽的下列資源類型的視覺化配置：

- Bitmap

- 對話方塊

- 圖示

- 功能表

- Cursor

- 工具列

視覺預覽函式不適用於加速器、 資訊清單、 字串資料表及版本資訊資源。

### <a name="to-preview-resources"></a>若要預覽資源

1. 在 [資源檢視](../windows/resource-view-window.md)或 [文件] 視窗中，選取您的資源，例如**IDD_ABOUTBOX**。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 在 [屬性](/visualstudio/ide/reference/properties-window)視窗，按一下**屬性頁** 按鈕。

   \-或-

3. 在 **檢視**功能表上，按一下**屬性頁**。

   **屬性頁**資源隨即開啟並顯示該資源的預覽。 然後您可以使用**向上**並**向下**方向鍵可瀏覽樹狀目錄控制項中**資源檢視**或文件視窗。 **屬性頁**會保持開啟，並顯示具有焦點，而且能夠預覽的任何資源。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[如何：在專案外開啟資源指令碼檔 (獨立式)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
[資源編輯器](../windows/resource-editors.md)