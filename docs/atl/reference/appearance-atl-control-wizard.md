---
title: 外觀，ATL 控制項精靈 |Microsoft Docs
ms.custom: ''
ms.date: 08/31/2018
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.misc
dev_langs:
- C++
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 132930c1ad7d4b9fc4ae9c3a875bbd2c6ec6f9d2
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755121"
---
# <a name="appearance-atl-control-wizard"></a>外觀, ATL 控制項精靈

在這裡插入 [搜尋結果] 摘要。

您可以使用精靈的這個頁面來識別控制項的其他使用者的項目選項。 此頁面可供控制項視為**標準控制項**下方**控制項類型**上[選項，ATL 控制項精靈](../../atl/reference/options-atl-control-wizard.md)頁面。

## <a name="uielement-list"></a>UIElement 清單

- **檢視狀態**

   設定容器內控制項的外觀。

   - **不透明**： 設定位元 VIEWSTATUS_OPAQUE [forced VIEWSTATUS](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus)列舉型別和繪製整個控制項矩形傳遞給[CComControlBase::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw)方法。 完全不透明的會出現這個控制項，並沒有任何容器顯示控制項界限後方。

      此設定可協助更快速地繪製控制項的容器。 如果未選取此選項，控制項可以包含透明的組件。

      只有不透明的控制項有單純的背景。

   - **單色背景**： 設定 VIEWSTATUS_SOLIDBKGND forced VIEWSTATUS 列舉中的位元。 控制項的背景會顯示為任何模式的純色。

      會提供這個選項才**不透明**也會選取選項。

- **新增控制項**

   設定以根據加上 Windows 控制項類型的控制項[CContainedWindow](ccontainedwindowt-class.md)實作控制項的類別資料成員。 此外，它也會新增訊息對應和訊息處理常式函式來處理控制項的 Windows 訊息。 從清單中選擇您想要建立此項目，如果有任何的 Windows 控制項的型別。

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

   設定其他控制項的外觀和行為選項。

   - **在執行階段不可見**： 設定要在執行階段是不可見的控制項。 您可以使用不可見的控制項來執行作業在背景中，例如定期引發事件。

   - **作用就像按鈕**： 設定位元 OLEMISC_ACTSLIKEBUTTON [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc)列舉型別，以控制来處理像是按鈕。 如果容器已標示為預設按鈕的控制項的用戶端站台，則選取此選項可讓您藉由繪製本身有較粗框架將本身顯示為預設按鈕的按鈕控制項。 請參閱[CComControlBase::GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault)如需詳細資訊。

   - **作用就像標籤**： 設定位元 OLEMISC 列舉 OLEMISC_ACTSLIKELABEL，若要啟用的控制項取代容器的原生的標籤。 容器會判斷該如何處理這個旗標，如果任何項目。

- **其他**

   設定控制項的其他行為選項。

   - **標準化 DC**： 設定控制項來建立標準化的裝置內容，當呼叫它來繪製本身。 這個動作會標準化控制項的外觀，但會讓繪製比較沒有效率。

   - **僅適用於視窗**： 指定您的控制項不能是無視窗。 如果您未選取此選項，您的控制項是支援無視窗物件的容器中會自動無視窗，而且自動視窗不支援無視窗物件的容器中。 選取此選項會強制您的控制項設為視窗型的即使支援無視窗物件的容器中。

   - **可插入**： 選取此選項可讓您的控制項中出現**插入物件**Word 和 Excel 等應用程式的對話方塊。 您的控制項則可以插入任何應用程式支援透過此對話方塊中的內嵌的物件。

## <a name="see-also"></a>另請參閱

[ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)<br/>
[SUBEDIT 範例： 超級類別的標準 Windows 控制項](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)

