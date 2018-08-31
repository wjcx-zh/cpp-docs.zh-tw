---
title: 將控制項加入至對話方塊會造成對話方塊無法再運作 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], troubleshooting
- common controls, troubleshooting
- troubleshooting controls
- dialog boxes, troubleshooting
- dialog box controls, troubleshooting
- InitCommonControls
ms.assetid: b2dd4574-ea59-4343-8d65-b387cead5da6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6d27c12b491fc5f05da58a84703ea13e84e9e9c6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215366"
---
# <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>將控制項加入至對話方塊會造成對話方塊無法使用

之後您可以將通用控制項或 rich edit 控制項加入對話方塊中，它不會出現測試對話方塊中，或將不會出現對話方塊本身時。

### <a name="example-of-the-problem"></a>問題範例

1. 建立 Win32 專案中，修改應用程式設定，讓您建立 Windows 應用程式 （而不將主控台應用程式）。

2. 在 [資源檢視](../windows/resource-view-window.md)，按兩下.rc 檔案。

3. 在 [對話方塊] 選項中，按兩下 [**關於**] 方塊中。

4. 新增**IP 位址控制項**對話方塊中。

5. 儲存並**重建所有**。

6. 執行此程式。

7. 在對話方塊中的**幫助** 功能表中，按一下**有關**命令; 沒有對話方塊會顯示。

### <a name="the-cause"></a>原因

目前，對話方塊編輯器不會不會自動加入程式碼至您的專案或您拖放的下列通用控制項 rich edit 控制項的對話方塊時。 也沒有 Visual Studio 提供錯誤或警告時就會發生此問題。 您必須手動加入控制項的程式碼。

||||
|-|-|-|
|滑桿控制項|樹狀目錄控制項|日期時間選擇器|
|微調控制項|索引標籤控制項|月份的行事曆|
|進度控制項|動畫控制項|IP 位址控制項|
|熱鍵|Rich Edit 控制項|擴充的下拉式方塊|
|清單控制項|Rich Edit 2.0 控制項|自訂控制項|

## <a name="the-fix-for-common-controls"></a>通用控制項的修正

若要使用通用控制項 對話方塊上的，您必須呼叫[InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex)或`AFXInitCommonControls`建立對話方塊之前。

## <a name="the-fix-for-richedit-controls"></a>修正、 RichEdit 控制項

您必須呼叫`LoadLibrary`rich edit 控制項的。 如需詳細資訊，請參閱 <<c0> [ 使用 RichEdit 1.0 控制項與 MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)，[有關 Rich Edit 控制項](/windows/desktop/Controls/about-rich-edit-controls)在 Windows SDK 中，並[Rich Edit 控制項的概觀](../mfc/overview-of-the-rich-edit-control.md)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊編輯器的疑難排解](../windows/troubleshooting-the-dialog-editor.md)  
[對話方塊編輯器](../windows/dialog-editor.md)