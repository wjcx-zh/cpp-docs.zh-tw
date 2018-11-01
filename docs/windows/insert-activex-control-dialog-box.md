---
title: 插入 ActiveX 控制項對話方塊 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- Insert ActiveX Control dialog box [C++]
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: 06638ea3-0726-40da-a989-9b89292d0e3d
ms.openlocfilehash: 495245141b62850067196c81bfe4c6f984dcfa88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592747"
---
# <a name="insert-activex-control-dialog-box-c"></a>插入 ActiveX 控制項對話方塊 （c + +）

此對話方塊可讓您[插入您的對話方塊中的 ActiveX 控制項](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)使用時[對話方塊編輯器](../windows/dialog-editor.md)。

### <a name="activex-control"></a>ActiveX 控制項

會顯示一份 Active X 控制項。 從這個對話方塊中插入控制項不會產生包裝函式類別。 如果您需要的包裝函數類別，使用[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)若要建立一個 (如需詳細資訊，請參閱[加入類別](../ide/adding-a-class-visual-cpp.md))。 如果 Active X 控制項不會出現在這個對話方塊中，再次嘗試安裝控制項根據廠商的指示。

### <a name="path"></a>路徑

顯示 ActiveX 控制項所在的檔案。

您可以放置在控制項**工具箱**視窗以方便存取。 如需詳細資訊，請參閱[工具箱](/visualstudio/ide/reference/)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[工具箱、對話方塊編輯器索引標籤](../windows/dialog-editor-tab-toolbox.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)