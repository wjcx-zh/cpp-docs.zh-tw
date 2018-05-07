---
title: MFC ActiveX 控制項精靈、 控制項設定 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.settings
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2161cea739d918bc0f5772a6cb08c29082a6e670
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="control-settings-mfc-activex-control-wizard"></a>MFC ActiveX 控制項精靈、控制項設定
使用精靈的這個頁面，指定控制項的行為方式。 比方說，您可以將基底控制項類型的標準 Windows 控制項、 最佳化其行為和外觀，或表示控制項可以做為其他控制項的容器。  
  
 如需如何選取此頁面上將控制項的效率最佳化的選項的詳細資訊，請參閱[MFC ActiveX 控制項： 最佳化](../../mfc/mfc-activex-controls-optimization.md)。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **建立控制項基礎**  
 在此清單中，您可以選取控制項應該從它繼承的控制項的類型。 清單是可供使用的控制項類別的子集`CreateWindowEx`和其他 commctrl.h 中指定的通用控制項。 您的選擇會決定在控制項的樣式`PreCreateWindow`函式在*ProjName*Ctrl.cpp 檔案。 如需詳細資訊，請參閱[MFC ActiveX 控制項： 子類別化 Windows 控制項](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。  
  
|控制項|描述|  
|-------------|-----------------|  
|**按鈕**|Windows 按鈕控制項|  
|**下拉式方塊**|Windows 下拉式方塊控制項|  
|**編輯**|Windows 編輯控制項|  
|**清單方塊**|Windows 清單方塊控制項|  
|**捲軸**|Windows 捲軸控制項|  
|**靜態**|Windows 靜態控制項|  
|**msctls_hotkey32**|熱鍵通用控制項|  
|**msctls_progress32**|進度列，通用控制項|  
|**msctls_statusbar32**|狀態列通用控制項|  
|**msctls_trackbar32**|滑動軸通用控制項|  
|**msctls_updown32**|微調按鈕 （或上下） 通用控制項|  
|**SysAnimate32**|動畫通用控制項|  
|**SysHeader32**|標頭的通用控制項|  
|**SysListView32**|清單檢視通用控制項|  
|**SysTabControl32**|索引標籤上的通用控制項|  
|**SysTreeView32**|樹狀結構檢視通用控制項|  
  
 **當可見時啟動**  
 指定存取時，為控制項建立視窗。 根據預設，**當可見時啟動**選取選項。 如果您想要延遲啟動控制項，直到容器需要它 （例如，當使用者按一下滑鼠），請清除此選項。 關閉這項功能時，控制項不會造成視窗建立費用直到必要為止。 如需詳細資訊，請參閱[關閉可見時啟動選項](../../mfc/turning-off-the-activate-when-visible-option.md)。  
  
 **在執行階段不可見**  
 指定控制項在執行期間有任何使用者介面。 計時器會是控制項的一種您可能想要隱藏。  
  
 **有關於對話方塊**  
 指定控制項有標準的 Windows**有關**對話方塊中，會顯示版本號碼和著作權資訊。  
  
> [!NOTE]
>  使用者如何存取控制項的說明取決於說明的實作方式，以及是否已整合該控制項的說明與容器說明。 如需有關如何整合的說明，請在[MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542)網站中，搜尋 「 加入即時線上說明以 MFC ActiveX 控制項 」。  
  
 當您選取此選項時，它會插入`AboutBox`控制方法在專案的控制項類別 (C*ProjName*Ctrl.cpp)，並將專案分派對應至 AboutBox。 根據預設，這個選項是選取的。  
  
 **最佳化繪製程式碼**  
 指定容器還原原始的 GDI 物件會自動在所有容器控制項中，會繪製到相同的裝置內容，已繪製。 如需有關這項功能的詳細資訊，請參閱[最佳化控制項繪圖](../../mfc/optimizing-control-drawing.md)。  
  
 **無視窗啟用**  
 指定的控制項不會產生視窗時啟動它。 無視窗啟用可讓非矩形或透明的控制項，並將無視窗控制項需要較少的系統額外負荷比具有視窗的控制項需要。 將無視窗控制項未裁剪的裝置內容或閃動不允許。 1996 年之前所建立的容器不支援無視窗啟用。 如需如何使用這個選項的詳細資訊，請參閱[提供無視窗啟用](../../mfc/providing-windowless-activation.md)。  
  
 **裁剪的裝置內容**  
 覆寫[Clippaintdc](../../mfc/reference/colecontrol-class.md#getcontrolflags)中控制標頭 (*projname*ctrl.h) 若要停用呼叫`IntersectClipRect`所做的`COleControl`。 當您選取此選項時，其好處是小型的速度。 如果您選取**無視窗啟用**，則無法使用此功能。 如需詳細資訊，請參閱[使用未裁剪的裝置內容](../../mfc/using-an-unclipped-device-context.md)。  
  
 **閃動**  
 排除繪製作業和控制項的作用中和非使用中狀態之間進行的視覺重繪。 如果您選取**無視窗啟用**，則無法使用此功能。 當您設定此選項，`noFlickerActivate`旗標是所傳回的旗標的其中一個[Clippaintdc](../../mfc/reference/colecontrol-class.md#getcontrolflags)。 如需詳細資訊，請參閱[提供閃動](../../mfc/providing-flicker-free-activation.md)。  
  
 **用於插入物件對話方塊**  
 指定控制項是否會用於**插入物件**啟用狀態的容器 對話方塊。 當您選取此選項，`afxRegInsertable`旗標是所傳回的旗標的其中一個`AfxOleRegisterControlClass`。 使用**插入物件**對話方塊中，使用者就可以插入新建或現有的物件至複合文件。  
  
 **非現用時滑鼠指標告知**  
 控制是否使用中，或不會啟用處理滑鼠指標告知，來控制。 當您選取此選項，`pointerInactive`旗標是所傳回的旗標的其中一個[Clippaintdc](../../mfc/reference/colecontrol-class.md#getcontrolflags)。 如需如何使用這個選項的詳細資訊，請參閱[提供滑鼠互動而非使用中](../../mfc/providing-mouse-interaction-while-inactive.md)。  
  
 **做為簡單框架控制項**  
 指定控制項是其他控制項的容器，藉由設定`OLEMISC_SIMPLEFRAME`控制項位元。 如需詳細資訊，在[MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542)網站中，搜尋 「 簡單框架站台內含項目 」。  
  
 **以非同步方式載入屬性**  
 可讓任何先前非同步資料的重設，並起始新載入控制項非同步屬性。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項精靈](../../mfc/reference/mfc-activex-control-wizard.md)   
 [MFC ActiveX 控制項精靈、 應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [MFC ActiveX 控制項精靈、控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)

