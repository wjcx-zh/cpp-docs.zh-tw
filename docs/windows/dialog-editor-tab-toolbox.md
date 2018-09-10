---
title: 對話方塊編輯器索引標籤上，工具箱 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
ms.assetid: 253885c2-dcb9-4d8e-ac9b-805ea31cbf5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2fa16a2cf15d5004ff80dda3188d79ffcba72ec1
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316207"
---
# <a name="dialog-editor-tab-toolbox-c"></a>對話方塊編輯器索引標籤上，工具箱 （c + +）

**對話方塊編輯器**索引標籤會出現在[工具箱視窗](/visualstudio/ide/reference/toolbox)當您處理**對話方塊**編輯器。 若要將控制項加入新的對話方塊中，將控制項從**工具箱**對話方塊中，您要建立 (如需詳細資訊，請參閱[將控制項加入對話方塊](adding-a-control-to-a-dialog-box.md))。 然後移動控制項，或變更其大小和形狀。

中可用的標準控制項**工具箱**是：

- [按鈕控制項](../mfc/reference/cbutton-class.md)

- [核取方塊控制項](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [下拉式方塊控制項](../mfc/reference/ccombobox-class.md)

- [編輯控制項](../mfc/reference/cedit-class.md)

- 群組方塊

- [清單方塊控制項](../mfc/reference/clistbox-class.md)

- [選項按鈕控制項](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [靜態文字控制項](../mfc/reference/cstatic-class.md)

- [圖片控制項](../mfc/reference/cpictureholder-class.md)

- [Rich Edit 2.0 控制項](../mfc/using-cricheditctrl.md)

- [捲軸控制項](../mfc/reference/cscrollbar-class.md)

[Windows 通用控制項](../mfc/controls-mfc.md)中可用**工具箱**提供增強的功能，在您的應用程式。 包括：

- [滑桿控制項](../mfc/slider-control-styles.md)

- [微調控制項](../mfc/using-cspinbuttonctrl.md)

- [進度控制項](../mfc/styles-for-the-progress-control.md)

- [熱鍵控制項](../mfc/using-a-hot-key-control.md)

- [清單控制項](../mfc/list-control-and-list-view.md)

- [樹狀目錄控制項](../mfc/tree-control-styles.md)

- [索引標籤控制項](../mfc/tab-controls-and-property-sheets.md)

- [動畫控制項](../mfc/using-an-animation-control.md)

- [日期時間選擇器控制項](../mfc/creating-the-date-and-time-picker-control.md)

- [月曆控制項](../mfc/month-calendar-control-examples.md)

- [IP 位址控制項](../mfc/reference/cipaddressctrl-class.md)

- [擴充的下拉式方塊控制項](../mfc/creating-an-extended-combo-box-control.md)

- [自訂控制項](custom-controls-in-the-dialog-editor.md)

您可以將自訂控制項加入對話方塊中選取**自訂控制項**中的圖示**工具箱**將它拖曳至您的對話方塊。 若要新增**Syslink**控制項，加入自訂控制項，然後變更控制項的**類別**屬性設**Syslink**。 這會導致要重新整理和顯示的屬性**Syslink**控制屬性。 如需 MFC 包裝函式類別的資訊，請參閱[CLinkCtrl](../mfc/reference/clinkctrl-class.md)。

您也可以[ActiveX 控制項加入您的對話方塊](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)。

您也可以自訂**工具箱**，方便使用的視窗。 如需詳細資訊，請參閱[使用工具箱](/visualstudio/ide/using-the-toolbox)。

如需有關使用**RichEdit 1.0**控制項與 MFC，請參閱[使用 RichEdit 1.0 控制項與 MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[控制項](../mfc/controls-mfc.md)  
[控制項類別](../mfc/control-classes.md)  
[對話方塊類別](../mfc/dialog-box-classes.md)  
[捲軸樣式](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)  
[Rich Edit 控制項範例](../mfc/rich-edit-control-examples.md)  
[加入對話方塊控制項的事件處理常式](../windows/adding-event-handlers-for-dialog-box-controls.md)  
[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)