---
title: "CStatusBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
dev_langs:
- C++
helpviewer_keywords:
- indicators, status bar
- CStatusBar class
- status bars
- indicators
- status indicators
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
caps.latest.revision: 24
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
ms.sourcegitcommit: b790beb88de009e1c7161f3c9af6b3e21c22fd8e
ms.openlocfilehash: a2358d31bd87b2cc540dd9a5ce182b9340764522
ms.lasthandoff: 03/29/2017

---
# <a name="cstatusbar-class"></a>CStatusBar 類別
具有一列文字輸出窗格或「指示器」的控制列。  
  
## <a name="syntax"></a>語法  
  
```  
class CStatusBar : public CControlBar  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CStatusBar::CStatusBar](#cstatusbar)|建構 `CStatusBar` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CStatusBar::CommandToIndex](#commandtoindex)|取得索引的指定的指標的識別碼。|  
|[CStatusBar::Create](#create)|建立狀態列，將它附加至`CStatusBar`物件，並設定初始的字型和列高度。|  
|[CStatusBar::CreateEx](#createex)|建立`CStatusBar`具有其他樣式為內嵌物件`CStatusBarCtrl`物件。|  
|[CStatusBar::DrawItem](#drawitem)|當主控描繪狀態列控制項會變更的視覺外觀時呼叫。|  
|[CStatusBar::GetItemID](#getitemid)|取得指定索引指標識別碼。|  
|[CStatusBar::GetItemRect](#getitemrect)|取得顯示給定索引的矩形。|  
|[CStatusBar::GetPaneInfo](#getpaneinfo)|取得指定索引的指標 ID、 樣式和寬度。|  
|[CStatusBar::GetPaneStyle](#getpanestyle)|取得指定索引的指標樣式。|  
|[CStatusBar::GetPaneText](#getpanetext)|取得指定索引指標文字。|  
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|允許直接存取基礎的通用控制項。|  
|[CStatusBar::SetIndicators](#setindicators)|設定指標的識別碼。|  
|[CStatusBar::SetPaneInfo](#setpaneinfo)|設定指標 ID、 樣式和特定索引的寬度。|  
|[CStatusBar::SetPaneStyle](#setpanestyle)|設定給定索引的指標樣式。|  
|[CStatusBar::SetPaneText](#setpanetext)|設定給定索引的標記文字。|  
  
## <a name="remarks"></a>備註  
 輸出窗格通常用來做為訊息列和狀態指示器。 範例包括簡要說明選取的功能表命令的功能表說明訊息行和顯示 SCROLL LOCK、 NUM LOCK 和其他按鍵的狀態指標。  
  
 [CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)，成員函式新增到 MFC 4.0 可讓您利用狀態列自訂和其他功能的 Windows 通用控制項的支援。 `CStatusBar`成員函式可讓您大部分的 Windows 通用控制項; 功能不過，當您呼叫`GetStatusBarCtrl`，您就能給予您狀態列更多 Windows 95/98 狀態列的特性。 當您呼叫`GetStatusBarCtrl`，它會傳回參考`CStatusBarCtrl`物件。 請參閱[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)如需有關設計 Windows 通用控制項的工具列。 關於通用控制項的一般資訊，請參閱[通用控制項](http://msdn.microsoft.com/library/windows/desktop/bb775493)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 架構將標記資訊儲存至位置 0 的最左邊指標的陣列。 當您建立狀態列時，您可以使用字串 Id，架構會將以相對應的指標的陣列。 您接著可以使用字串識別碼或索引來存取指標。  
  
 根據預設，第一個指標是 「 彈性 」: 使其他窗格靠右對齊，因此會佔用狀態列長度不供其他指標窗格。  
  
 若要建立狀態列，請遵循下列步驟︰  
  
1.  建構 `CStatusBar` 物件。  
  
2.  呼叫[建立](#create)(或[CreateEx](#createex)) 函式來建立狀態列 視窗，並將其附加至`CStatusBar`物件。  
  
3.  呼叫[SetIndicators](#setindicators)字串 ID 與每一個指標。  
  
 有三種方法來更新狀態列窗格中的文字︰  
  
1.  呼叫[CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)更新窗格僅 0 中的文字。  
  
2.  呼叫[CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext)在狀態列上`ON_UPDATE_COMMAND_UI`處理常式。  
  
3.  呼叫[SetPaneText](#setpanetext)更新任何窗格的文字。  
  
 呼叫[SetPaneStyle](#setpanestyle)更新狀態列窗格的樣式。  
  
 如需有關使用`CStatusBar`，請參閱文章[狀態在 MFC 中的列實作](../../mfc/status-bar-implementation-in-mfc.md)和[技術提示 31︰ 控制列](../../mfc/tn031-control-bars.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CStatusBar`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxext.h  
  
##  <a name="commandtoindex"></a>CStatusBar::CommandToIndex  
 指示器索引取得指定的識別碼。  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIDFind`  
 指標的索引是要擷取的字串識別碼。  
  
### <a name="return-value"></a>傳回值  
 指標成功; 如果索引如果不成功-1。  
  
### <a name="remarks"></a>備註  
 第一個指標的索引為 0。  
  
##  <a name="create"></a>CStatusBar::Create  
 建立狀態列 （子視窗），並將它與相關聯`CStatusBar`物件。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>參數  
 `pParentWnd`  
 指標[CWnd](../../mfc/reference/cwnd-class.md)其 Windows 視窗中是 [狀態] 列的父代的物件。  
  
 `dwStyle`  
 狀態列樣式。 除了標準 Windows[樣式](../../mfc/reference/window-styles.md)，支援這些樣式。  
  
- `CBRS_TOP`控制列是在框架視窗的頂端。  
  
- `CBRS_BOTTOM`控制列是在框架視窗的底部。  
  
- `CBRS_NOALIGN`父代重新調整大小時未重新置放控制列。  
  
 `nID`  
 工具列的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 也設定初始的字型，並將狀態設定為預設值的長條的高度。  
  
##  <a name="createex"></a>CStatusBar::CreateEx  
 呼叫此函式可建立狀態列 （子視窗），並將它與相關聯`CStatusBar`物件。  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>參數  
 `pParentWnd`  
 指標[CWnd](../../mfc/reference/cwnd-class.md)其 Windows 視窗中是 [狀態] 列的父代的物件。  
  
 `dwCtrlStyle`  
 建立內嵌的其他樣式[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)物件。 預設值會指定狀態列，而不需要調整大小底框或工具提示支援。 支援的狀態 列樣式為︰  
  
- **SBARS_SIZEGRIP**狀態列控制項包含 [狀態] 列右邊的調整大小底框。 調整大小的底框類似縮放框線；它是使用者可以按一下並拖曳調整父視窗大小的矩形區域。  
  
- **SBT_TOOLTIPS**狀態列支援工具提示。  
  
 如需有關這些樣式的詳細資訊，請參閱[CStatusBarCtrl 的設定](../../mfc/settings-for-the-cstatusbarctrl.md)。  
  
 `dwStyle`  
 狀態的橫條樣式。 預設值會指定顯示狀態列，建立框架視窗的底部。 套用狀態列控制項樣式中所列的任何組合[視窗樣式](../../mfc/reference/window-styles.md)和[CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create)。 不過，這個參數應該永遠包含 WS_CHILD 和 WS_VISIBLE 樣式。  
  
 `nID`  
 [狀態] 列的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式也會設定初始的字型，並將狀態設定為預設值的長條的高度。  
  
 使用`CreateEx`，而不是[建立](#create)，當特定樣式必須要有內嵌的狀態列控制項建立期間。 例如，設定`dwCtrlStyle`至**SBT_TOOLTIPS**顯示狀態 列物件中的工具提示。  
  
##  <a name="cstatusbar"></a>CStatusBar::CStatusBar  
 建構`CStatusBar`物件、 建立預設狀態列字型如有必要，，並設定為預設值的字型特性。  
  
```  
CStatusBar();
```  
  
##  <a name="drawitem"></a>CStatusBar::DrawItem  
 當主控描繪狀態列會變更的視覺外觀的架構會呼叫此成員函式。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDrawItemStruct`  
 指標[DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802)結構，其中包含所需的繪圖的類型資訊。  
  
### <a name="remarks"></a>備註  
 **ItemAction**隸屬`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。 覆寫此成員函式，來實作主控描繪的繪圖`CStatusBar`物件。 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件`lpDrawItemStruct`之前終止此成員函式。  
  
##  <a name="getitemid"></a>CStatusBar::GetItemID  
 傳回所指定的標記識別碼`nIndex`。  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指標的識別碼是要擷取的索引。  
  
### <a name="return-value"></a>傳回值  
 指標所指定的識別碼`nIndex`。  
  
##  <a name="getitemrect"></a>CStatusBar::GetItemRect  
 複製指標所指定的座標`nIndex`至所指向的結構`lpRect`。  
  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要擷取其矩形座標的指標的索引。  
  
 `lpRect`  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，將會收到指標所指定的座標`nIndex`。  
  
### <a name="remarks"></a>備註  
 座標是相對於狀態列的左上角像素為單位。  
  
##  <a name="getpaneinfo"></a>CStatusBar::GetPaneInfo  
 設定`nID`， `nStyle`，和`cxWidth`至 ID、 樣式和寬度所指定的位置指標窗格的`nIndex`。  
  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要擷取其資訊 窗格的索引。  
  
 `nID`  
 若要參考**UINT**設窗格的識別碼。  
  
 `nStyle`  
 若要參考**UINT**為樣式 窗格的設定。  
  
 `cxWidth`  
 參考設定為窗格的寬度的整數。  
  
##  <a name="getpanestyle"></a>CStatusBar::GetPaneStyle  
 呼叫此成員函式可擷取的狀態列窗格的樣式。  
  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要擷取其樣式 窗格的索引。  
  
### <a name="return-value"></a>傳回值  
 [狀態列] 窗格中所指定的樣式`nIndex`。  
  
### <a name="remarks"></a>備註  
 窗格的樣式會決定如何顯示 窗格。  
  
 如需可用狀態列樣式的清單，請參閱[建立](#create)。  
  
##  <a name="getpanetext"></a>CStatusBar::GetPaneText  
 呼叫此成員函式可擷取狀態列窗格中顯示的文字。  
  
```  
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要擷取其文字窗格的索引。  
  
 `rString`  
 若要參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含要擷取的文字。  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，其中包含窗格的文字。  
  
### <a name="remarks"></a>備註  
 這個成員的第二個表單函式的填滿`CString`具有字串文字物件。  
  
##  <a name="getstatusbarctrl"></a>CStatusBar::GetStatusBarCtrl  
 此成員函式可讓您直接存取基礎的通用控制項。  
  
```  
CStatusBarCtrl& GetStatusBarCtrl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含參考[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)物件。  
  
### <a name="remarks"></a>備註  
 使用`GetStatusBarCtrl`充分利用 Windows 狀態列通用控制項的功能，並利用支援[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)提供狀態列可自訂的。 例如，使用通用控制項，您可以指定包含在狀態列上，調整大小底框樣式，或您可以指定將出現在父視窗工作區頂端的 [狀態] 列的樣式。  
  
 關於通用控制項的一般資訊，請參閱[通用控制項](http://msdn.microsoft.com/library/windows/desktop/bb775493)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setindicators"></a>CStatusBar::SetIndicators  
 陣列的對應項目所指定的值來設定每一個指標 ID `lpIDArray`、 載入每個識別碼，由指定之字串資源，並將指標的文字設為字串。  
  
```  
BOOL SetIndicators(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>參數  
 `lpIDArray`  
 識別碼的陣列指標。  
  
 `nIDCount`  
 所指陣列中的項目數`lpIDArray`。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
##  <a name="setpaneinfo"></a>CStatusBar::SetPaneInfo  
 將指定的指標窗格設定為新的 ID、 樣式和寬度。  
  
```  
void SetPaneInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int cxWidth);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要設定其樣式指標窗格的索引。  
  
 `nID`  
 [指標] 窗格中的新識別碼。  
  
 `nStyle`  
 [指標] 窗格中的新樣式。  
  
 `cxWidth`  
 新的指標窗格的寬度。  
  
### <a name="remarks"></a>備註  
 支援下列指標樣式︰  
  
- **SBPS_NOBORDERS**窗格沒有 3d 框線。  
  
- **SBPS_POPOUT**反向框線，讓文字 」 會跳出。 」  
  
- **SBPS_DISABLED**不繪製文字。  
  
- **SBPS_STRETCH** Stretch 窗格，以填滿未使用的空間。 只有每個狀態列上一個窗格可以將此樣式。  
  
- **SBPS_NORMAL**沒有 stretch、 框線或快顯。  
  
##  <a name="setpanestyle"></a>CStatusBar::SetPaneStyle  
 呼叫此成員函式，設定狀態列窗格的樣式。  
  
```  
void SetPaneStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 若要設定其樣式 窗格的索引。  
  
 `nStyle`  
 若要設定其樣式 窗格的樣式。  
  
### <a name="remarks"></a>備註  
 窗格的樣式會決定如何顯示 窗格。  
  
 如需可用狀態列樣式的清單，請參閱[SetPaneInfo](#setpaneinfo)。  
  
##  <a name="setpanetext"></a>CStatusBar::SetPaneText  
 呼叫此成員函式，將窗格文字所指向的字串為`lpszNewText`。  
  
```  
BOOL SetPaneText(
    int nIndex,  
    LPCTSTR lpszNewText,  
    BOOL bUpdate = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要設定其文字窗格的索引。  
  
 `lpszNewText`  
 新的窗格中文字指標。  
  
 *bUpdate*  
 如果**TRUE**，窗格失效之後設定文字。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 在您呼叫後`SetPaneText`，您必須新增 UI 更新處理常式，以在狀態列中顯示新的文字。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView # 177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView # 178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CTRLBARS](../../visual-cpp-samples.md)   
 [MFC 範例 DLGCBR32](../../visual-cpp-samples.md)   
 [CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CStatusBarCtrl 類別](../../mfc/reference/cstatusbarctrl-class.md)   
 [CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)

