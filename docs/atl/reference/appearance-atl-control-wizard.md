---
title: "外觀、 ATL 控制項精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.misc
dev_langs:
- C++
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: dde27a7b62f3ee3b5fe8fcacd8141e9f89ed3c98
ms.lasthandoff: 02/24/2017

---
# <a name="appearance-atl-control-wizard"></a>外觀, ATL 控制項精靈
在這裡插入摘要的 「 搜尋結果 」。  
  
 使用精靈的這個頁面來識別控制項的其他使用者項目選項。 此頁面是可用的控制項識別為**標準控制項**下**控制類型**上[選項、 ATL 控制項精靈](../../atl/reference/options-atl-control-wizard.md)頁面。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **檢視狀態**  
 設定容器中控制項的外觀。  
  
-   **不透明**︰ 設定`VIEWSTATUS_OPAQUE`位元[forced VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201)列舉型別和繪製整個控制項的矩形傳遞至[CComControlBase::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw)方法。 控制項會出現完全不透明，以及任何容器控制項界限會顯示。  
  
     此設定可協助更快速地繪製控制項的容器。 如果未選取此選項，控制項可以包含透明的組件。  
  
     只有不透明的控制項有透明背景。  
  
-   設定`VIEWSTATUS_SOLIDBKGND`位元`VIEWSTATUS`列舉型別。 控制項的背景會顯示為純色沒有固定的模式。  
  
     會提供這個選項才**不透明**也會選取選項。  
  
 **加入控制項**  
 設定是根據 Windows 控制項類型加入控制項[CContainedWindow](ccontainedwindowt-class.md)来實作控制項的類別資料成員。 它也會新增訊息對應和訊息處理常式函式來處理控制項的視窗訊息。 從清單中選擇您想要建立時，如果有任何的 Windows 控制項的類型。  

  
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
  
-   **在執行階段不可見**︰ 設定要在執行階段是不可見的控制項。 您可以使用不可見的控制項來執行作業，在背景中，例如在固定間隔引發事件。  
  
-   **作用就像按鈕**︰ 設定`OLEMISC_ACTSLIKEBUTTON`位元[OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)列舉型別，若要啟用控制項的作用像是按鈕。 如果容器已標示為預設按鈕控制項的用戶端站台，選取此選項可讓您使其具有較粗的框架繪製其顯示為預設按鈕的按鈕控制項。 請參閱[CComControlBase::GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault)如需詳細資訊。  
  
-   **作用就像標籤**︰ 設定`OLEMISC_ACTSLIKELABEL`位元`OLEMISC`列舉型別，以控制，以取代容器的原生的標籤。 容器會決定如何處理這個旗標，如果任何項目。  
  
 **其他**  
 設定控制項的其他行為的選項。  
  
-   **正規化 DC**︰ 設定要建立標準化的裝置內容時呼叫它來繪製本身的控制項。 這個動作會標準化控制項的外觀，但會讓繪製效率較差。  
  
-   **僅適用於視窗**︰ 指定不能是無視窗控制項。 如果您未選取此選項，您的控制項是自動無視窗支援無視窗物件的容器中，而且很自動視窗中不支援無視窗物件的容器。 選取此選項會強制控制項視窗時，即使支援無視窗物件的容器中。  
  
-   **可插入**︰ 選取此選項可讓您的控制項出現在**插入物件**Word 和 Excel 等應用程式 對話方塊。 您的控制項則可以插入任何支援內嵌的物件，透過此對話方塊中的應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)   
 [SUBEDIT 範例︰ 是標準的 Windows 控制項](http://msdn.microsoft.com/en-us/30e46bdc-ed92-417c-b6b8-359017265a7b)


