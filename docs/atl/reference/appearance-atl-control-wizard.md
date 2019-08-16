---
title: 外觀, ATL 控制項精靈
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: e07dc017241848f1a670c17b12c2254de6d1b8e1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492179"
---
# <a name="appearance-atl-control-wizard"></a>外觀, ATL 控制項精靈

使用嚮導的這個頁面, 即可識別控制項的其他使用者元素選項。 此頁面適用于在 [[選項]、[ATL 控制項嚮導]](../../atl/reference/options-atl-control-wizard.md)頁面上, 識別為 [**控制項類型**] 下的 [**標準] 控制項**的控制項。

## <a name="uielement-list"></a>UIElement 清單

- **檢視狀態**

   設定容器內控制項的外觀。

   - 不**透明**:在[VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus)列舉中設定 VIEWSTATUS_OPAQUE 位, 並繪製傳遞至[CComControlBase:: OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw)方法的整個控制矩形。 控制項完全不透明, 而且不會在控制項界限後方顯示任何容器。

      此設定可協助容器更快速地繪製控制項。 如果未選取此選項, 控制項可以包含透明的部分。

      只有不透明的控制項可以具有純色背景。

   - **純色背景**:在 VIEWSTATUS 列舉中設定 VIEWSTATUS_SOLIDBKGND 位。 控制項的背景會顯示為純色, 不含任何模式。

      只有在同時選取 [不**透明**] 選項時, 才能使用此選項。

- **新增控制項依據**

   藉由將[CContainedWindow](ccontainedwindowt-class.md)資料成員加入至執行控制項的類別, 將控制項設定為以 Windows 控制項類型為基礎。 它也會加入訊息對應和訊息處理常式函式, 以處理控制項的 Windows 訊息。 從清單中選擇您想要建立的 Windows 控制項類型 (如果有的話)。

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

   - **Static**

   - **SysIPAddress32**

   - **SysTreeView32**

- **其他狀態**

   設定控制項的其他外觀和行為選項。

   - **執行時間不可見**:將控制項設定為在執行時間不可見。 您可以使用隱藏的控制項在背景中執行作業, 例如以計時間隔引發事件。

   - **作用類似按鈕**:在[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)列舉中設定 OLEMISC_ACTSLIKEBUTTON 位, 讓控制項的動作如同按鈕。 如果容器已將控制項的用戶端網站標示為預設按鈕, 則選取此選項可讓您的按鈕控制項以較寬的框架繪製其本身, 以將其本身顯示為預設按鈕。 如需詳細資訊, 請參閱[CComControlBase:: GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) 。

   - **作用如標籤**:在 OLEMISC 列舉中設定 OLEMISC_ACTSLIKELABEL 位, 讓控制項取代容器的原生標籤。 容器會決定要如何處理此旗標 (如果有的話)。

- **其他**

   設定控制項的其他行為選項。

   - **正規化 DC**:設定控制項, 以在呼叫以繪製本身時, 建立正規化的裝置內容。 此動作會將控制項的外觀標準化, 但會使繪製較不有效率。

   - **僅限視窗**:指定您的控制項不可為無視窗。 如果您未選取此選項, 您的控制項就會自動在支援無視窗物件的容器中執行無視窗, 而且它會自動在不支援無視窗物件的容器中視窗化。 選取此選項會強制您的控制項成為視窗型, 即使在支援無視窗物件的容器中也一樣。

   - **插入**:選取此選項, 讓控制項出現在 Word 和 Excel 等應用程式的 [**插入物件**] 對話方塊中。 然後, 可以透過這個對話方塊支援内嵌物件的任何應用程式, 插入您的控制項。

## <a name="see-also"></a>另請參閱

[ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)<br/>
[SUBEDIT 範例:標準 Windows 控制項的超類](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
