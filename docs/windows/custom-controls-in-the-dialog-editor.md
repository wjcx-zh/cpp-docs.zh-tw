---
title: 自訂控制項在對話方塊編輯器中 （c + +）
ms.date: 11/04/2016
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
ms.openlocfilehash: c48ad87948037fa843fdc16a016ae23bf139feb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677093"
---
# <a name="custom-controls-in-the-dialog-editor-c"></a>自訂控制項在對話方塊編輯器中 （c + +）

對話方塊編輯器可讓您使用現有 「 自訂 」 或對話方塊範本中的 「 使用者 」 控制項。

> [!NOTE]
> 在這種情況下的自訂控制項是不會混淆的 ActiveX 控制項。 ActiveX 控制項已有時也稱為 OLE 自訂控制項。 此外，請勿混淆主控描繪控制項在 Windows 中使用這些控制項。

這項功能被為了讓您使用所提供的 Windows 以外的控制項。 在執行階段，則控制項為相關聯的視窗類別 （不同於 c + + 類別）。 安裝在您的對話方塊中的任何控制項，例如靜態控制項，是較常見的方式，來完成相同的工作。 然後會在執行階段，在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函式，移除該控制項，並取代您自己的自訂控制項。

這是舊的技巧。 目前建議您在大部分情況下撰寫 ActiveX 控制項或子類別化 Windows 通用控制項。

這些自訂的控制項，您僅限於：

- 在對話方塊中設定的位置。

- 輸入標題。

- 用來識別控制項的 Windows 類別 （應用程式程式碼必須註冊該控制項使用這個名稱） 的名稱。

- 輸入 32 位元的十六進位值，設定控制項的樣式。

- 設定延伸的樣式。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[控制項](../mfc/controls-mfc.md)