---
title: 外觀, ATL 控制項精靈
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: 3484fb5d0f919af0dfd18b584e96d4675e2baea8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319401"
---
# <a name="appearance-atl-control-wizard"></a>外觀, ATL 控制項精靈

使用嚮導的此頁面標識控制項的其他使用者元素選項。 此頁面可用於在[「選項、ATL 控制精靈](../../atl/reference/options-atl-control-wizard.md)」頁上識別為 **「控制」類型**下**的標準控制項**。

## <a name="uielement-list"></a>UIElement 清單

- **檢視狀態**

   設置容器內控件的外觀。

  - **不透明**:設置[檢視狀態](/windows/win32/api/ocidl/ne-ocidl-viewstatus)枚舉中的VIEWSTATUS_OPAQUE位,並繪製傳遞給[CComControlBase::onDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw)方法的整個控制項矩形。 控件顯示為完全不透明,並且沒有任何容器顯示在控制邊界後面。

      此設置可説明容器更快地繪製控制件。 如果未選擇此選項,則控制項可以包含透明元件。

      只有不透明控制者才能具有實體背景。

  - **實體背景**:設置檢視狀態枚舉中的VIEWSTATUS_SOLIDBKGND位。 控件的背景顯示為純色,沒有圖案。

      僅當也選擇了 **「不透明」** 選項時,此選項才可用。

- **基於**

   通過將[CContainedWindow](ccontainedwindowt-class.md)數據成員添加到實現控制項的類,將控制項設定為基於 Windows 控制件類型。 它還添加消息映射和消息處理程式函數來處理控制件的 Windows 消息。 從清單中選擇要創建的 Windows 控制件的類型(如果有)。

  - **Button**

  - **ListBox**

  - **SysAnimate32**

  - **SysListView32**

  - **ComboBox**

  - **RichEdit**

  - **SysDateTimePick32**

  - **SysMonthCal32**

  - **ComboBoxEx32**

  - **ScrollBar**

  - **SysHeader32**

  - **SysTabControl32**

  - **編輯**

  - **靜態**

  - **SysIPAddress32**

  - **SysTreeView32**

- **雜項狀態**

   為控件設置其他外觀和行為選項。

  - **運行時不可見**:將控制項設定為運行時不可見。 可以使用不可見控制程式在後台執行操作,例如以時序間隔觸發事件。

  - **操作類似於按鈕**:在[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)枚舉中設置OLEMISC_ACTSLIKEBUTTON位,使控件能夠像按鈕一樣操作。 如果容器將控制項的用戶端站點標記為預設按鈕,則選擇此選項可使按鈕控制件透過使用較粗的框架繪製自身來將自己顯示為預設按鈕。 有關詳細資訊[,請參閱 CComControlBase:獲取環境顯示作為預設](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault)資訊。

  - **像標籤一樣:** 在 OLEMISC 枚舉中設置OLEMISC_ACTSLIKELABEL位,使控件能夠替換容器的本機標籤。 容器確定如何處理此標誌(如果有)。

- **其他**

   為控件設置其他行為選項。

  - **規範化 DC**: 設定控制項,在呼叫它繪製自身時創建規範化的裝置上下文。 此操作使控件的外觀標準化,但會使繪圖效率降低。

  - **僅視窗**:指定控制項不能無視窗。 如果不選擇此選項,控制件在支援無視窗物件的容器中自動無視窗,並且它會自動在不支援無視窗物件的容器中視窗。 選擇此選項將強制控制元件視窗化,即使在支援無視窗物件的容器中也是如此。

  - **可插入**:選擇此選項可使控制項顯示在「**插入物件」** 對話框中的應用程式(如 Word 和 Excel)中。 然後,任何支援嵌入物件的應用程式都可以通過此對話框插入您的控制項。

## <a name="see-also"></a>另請參閱

[ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)<br/>
[SUBEDIT 範例:超類標準 Windows 控制項](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
