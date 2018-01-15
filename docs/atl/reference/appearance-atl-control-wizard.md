---
title: "外觀，ATL 控制項精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.control.misc
dev_langs: C++
helpviewer_keywords: ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8869df577dfbc541b989beb4b4f3117d7d12feea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="appearance-atl-control-wizard"></a>外觀, ATL 控制項精靈
在這裡插入摘要的 「 搜尋結果 」。  
  
 使用精靈的這個頁面來識別控制項的其他使用者項目選項。 此頁面適用於控制項識別為**標準控制項**下**控制項類型**上[選項，ATL 控制項精靈](../../atl/reference/options-atl-control-wizard.md)頁面。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **檢視狀態**  
 設定容器內控制項的外觀。  
  
-   **不透明**： 集`VIEWSTATUS_OPAQUE`位元[forced VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201)列舉型別和繪製整個控制項矩形傳遞至[CComControlBase::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw)方法。 該控制項會出現完全不透明和任何容器控制項界限會顯示。  
  
     此設定可協助您更快速地繪製控制項的容器。 如果未選取此選項，此控制項可以包含透明的組件。  
  
     只有不透明的控制項可以有透明背景。  
  
-   設定`VIEWSTATUS_SOLIDBKGND`位元`VIEWSTATUS`列舉型別。 控制項的背景會顯示為純色任何模式。  
  
     會提供這個選項才**不透明**也會選取選項。  
  
 **加入控制項**  
 設定是根據 Windows 控制項類型所加入的控制項[CContainedWindow](ccontainedwindowt-class.md)来實作此控制項的類別資料成員。 此外，它也會加入訊息對應和訊息處理常式函式來處理控制項的視窗訊息。 從清單中選擇您想要建立時，如果有任何的 Windows 控制項的類型。  

  
-   `Button`  
  
-   `ListBox`  
  
-   `SysAnimate32`  
  
-   `SysListView32`  
  
-   `ComboBox`  
  
-   `RichEdit`  
  
-   `SysDateTimePick32`  
  
-   `SysMonthCal32`  
  
-   `ComboBoxEx32`  
  
-   `ScrollBar`  
  
-   `SysHeader32`  
  
-   `SysTabControl32`  
  
-   `Edit`  
  
-   `Static`  
  
-   `SysIPAddress32`  
  
-   `SysTreeView32`  
  
 **其他狀態**  
 設定其他控制項的外觀和行為選項。  
  
-   **在執行階段隱藏**： 設定要在執行階段是不可見的控制項。 您可以使用不可見的控制項在背景中，例如引發事件定期執行作業。  
  
-   **按鈕就像是**： 集`OLEMISC_ACTSLIKEBUTTON`位元[OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)列舉型別，以啟用控制項的作用類似按鈕。 如果容器已標示為預設按鈕控制項的用戶端站台，選取此選項可讓您的按鈕控制項來顯示本身為預設按鈕，藉由繪製本身粗框架。 請參閱[CComControlBase::GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault)如需詳細資訊。  
  
-   **標籤就像是**： 集`OLEMISC_ACTSLIKELABEL`位元`OLEMISC`列舉型別，以控制，以取代容器的原生的標籤。 容器會判斷該如何處理這個旗標，任何項目。  
  
 **其他**  
 設定控制項的其他行為的選項。  
  
-   **正規化 DC**： 設定控制項來繪製本身呼叫時，建立標準化的裝置內容。 這個動作會標準化控制項的外觀，但會讓繪製比較沒有效率。  
  
-   **僅適用於視窗**： 指定控制項不能是無視窗。 如果您未選取此選項，您的控制項已自動無視窗在容器中可支援無視窗物件，而自動視窗中不支援無視窗物件的容器。 選取此選項會強制您為視窗型的即使支援無視窗物件的容器中的控制項。  
  
-   **可插入**： 選取此選項可讓您的控制項出現在**插入物件**Word 和 Excel 之類的應用程式的對話方塊。 支援透過此對話方塊中的內嵌的物件的任何應用程式可以再插入您的控制項。  
  
## <a name="see-also"></a>請參閱  
 [ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)   
 [SUBEDIT 範例： Superclasses 標準 Windows 控制項](http://msdn.microsoft.com/en-us/30e46bdc-ed92-417c-b6b8-359017265a7b)

