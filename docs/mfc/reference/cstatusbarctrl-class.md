---
title: CStatusBarCtrl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
dev_langs:
- C++
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a555cc26e8857899690852743fa177a706afa0f2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677741"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl 類別
提供 Windows 通用狀態列控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CStatusBarCtrl : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|建構 `CStatusBarCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CStatusBarCtrl::Create](#create)|建立狀態列控制項，並將它附加至`CStatusBarCtrl`物件。|  
|[CStatusBarCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式中建立狀態列控制項，並將它附加至`CStatusBarCtrl`物件。|  
|[CStatusBarCtrl::DrawItem](#drawitem)|當主控描繪狀態列控制項會變更的視覺外觀時呼叫。|  
|[CStatusBarCtrl::GetBorders](#getborders)|擷取目前的狀態列控制項的水平和垂直框線的寬度。|  
|[CStatusBarCtrl::GetIcon](#geticon)|擷取目前狀態列控制項中的組件 （也稱為窗格） 圖示。|  
|[CStatusBarCtrl::GetParts](#getparts)|擷取狀態列控制項中的組件的計數。|  
|[CStatusBarCtrl::GetRect](#getrect)|擷取狀態列控制項中的組件的週框矩形。|  
|[Cstatusbarctrl:: Gettext](#gettext)|狀態列控制項的指定部分從擷取的文字。|  
|[Cstatusbarctrl:: Gettextlength](#gettextlength)|擷取的長度，以從狀態列控制項的指定部分文字的字元為單位。|  
|[Cstatusbarctrl:: Gettiptext](#gettiptext)|擷取中的狀態列窗格的工具提示文字。|  
|[CStatusBarCtrl::IsSimple](#issimple)|檢查以判斷它是否在簡單模式下的狀態視窗控制項。|  
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|在狀態列中設定的背景色彩。|  
|[CStatusBarCtrl::SetIcon](#seticon)|在狀態列中設定窗格圖示。|  
|[CStatusBarCtrl::SetMinHeight](#setminheight)|設定狀態的最小高度列控制項的繪圖區域。|  
|[CStatusBarCtrl::SetParts](#setparts)|設定組件中的狀態列控制項，而每個部分的右邊緣的座標。|  
|[CStatusBarCtrl::SetSimple](#setsimple)|指定狀態列控制項是否會顯示簡單的文字，或顯示所有先前呼叫所設定的控制項組件`SetParts`。|  
|[CStatusBarCtrl::SetText](#settext)|在狀態列控制項的指定部分設定文字。|  
|[Cstatusbarctrl:: Settiptext](#settiptext)|設定工具提示文字窗格的 [狀態] 列中。|  
  
## <a name="remarks"></a>備註  
 「 狀態列 」 是水平的視窗中，通常會顯示在底部的 [父] 視窗中，以何種應用程式可以顯示各種狀態資訊。 狀態列控制項可以分割成組件來顯示多個類型的資訊。  
  
 這個控制項 (並因此`CStatusBarCtrl`類別) 僅適用於 Windows 95/98 和 Windows NT 版 3.51 下執行的程式和更新版本。  
  
 如需有關使用`CStatusBarCtrl`，請參閱 <<c2> [ 控制項](../../mfc/controls-mfc.md)並[使用 CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatusBarCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="create"></a>  CStatusBarCtrl::Create  
 建立狀態列控制項，並將它附加至`CStatusBarCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *cheaderctrl:: Create*  
 指定狀態列控制項的樣式。 套用狀態列控制項的樣式中所列的任何組合[常見的控制項樣式](/windows/desktop/Controls/common-control-styles)Windows SDK 中。 這個參數必須包含 WS_CHILD 樣式。 它也應該包括 WS_VISIBLE 樣式。  
  
 *rect*  
 指定狀態列控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
 *pParentWnd*  
 指定狀態列控制項的父視窗，通常`CDialog`。 它必須不是 NULL。  
  
 *nID*  
 指定狀態列控制項的識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CStatusBarCtrl`兩個步驟。 首先，呼叫建構函式，並接著呼叫`Create`，這會建立狀態列控制項，並將它附加至`CStatusBarCtrl`物件。  
  
 狀態視窗的預設位置是在父視窗的底部，但是您可以指定要讓它出現在父視窗的工作區頂端的 CCS_TOP 樣式。 您可以指定要包含在狀態視窗的右端的調整大小底框的 SBARS_SIZEGRIP 樣式。 不建議結合 CCS_TOP 和 SBARS_SIZEGRIP 樣式，因為產生的調整大小底框不能運作，即使系統將它繪製在狀態視窗。  
  
 若要建立延伸的視窗樣式的狀態列，呼叫[CStatusBarCtrl::CreateEx](#createex)而不是`Create`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>  CStatusBarCtrl::CreateEx  
 建立控制項 （子視窗），並將它與關聯`CStatusBarCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *dwExStyle*  
 指定正在建立之控制項的延伸的樣式。 如需延伸的 Windows 樣式的清單，請參閱 < *dwExStyle*參數[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。  
  
 *cheaderctrl:: Create*  
 指定狀態列控制項的樣式。 套用狀態列控制項的樣式中所列的任何組合[常見的控制項樣式](/windows/desktop/Controls/common-control-styles)Windows SDK 中。 這個參數必須包含 WS_CHILD 樣式。 它也應該包括 WS_VISIBLE 樣式。  
  
 *rect*  
 參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置，在中建立工作區座標中的視窗*pParentWnd*。  
  
 *pParentWnd*  
 是控制項的父視窗的指標。  
  
 *nID*  
 控制項的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而非[建立](#create)套用延伸的 Windows 樣式，由 Windows 延伸的樣式前置詞**WS_EX_**。  
  
##  <a name="cstatusbarctrl"></a>  CStatusBarCtrl::CStatusBarCtrl  
 建構 `CStatusBarCtrl` 物件。  
  
```  
CStatusBarCtrl();
```  
  
##  <a name="drawitem"></a>  CStatusBarCtrl::DrawItem  
 當主控描繪狀態列控制項會變更的視覺外觀時，架構呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 *lpDrawItemStruct*  
 長指標[DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct)結構，其中包含的所需的繪圖類型的相關資訊。  
  
### <a name="remarks"></a>備註  
 `itemAction`隸屬`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。  
  
 根據預設，此成員函式沒有任何作用。 覆寫此成員函式，來實作活動，抽獎獲得主控描繪`CStatusBarCtrl`物件。  
  
 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件*lpDrawItemStruct*之前此成員函式會結束。  
  
##  <a name="getborders"></a>  CStatusBarCtrl::GetBorders  
 擷取狀態列控制項的目前寬度的水平和垂直框線和矩形之間的間距。  
  
```  
BOOL GetBorders(int* pBorders) const;  
  
BOOL GetBorders(
    int& nHorz,  
    int& nVert,  
    int& nSpacing) const;  
```  
  
### <a name="parameters"></a>參數  
 *pBorders*  
 有三個元素的整數陣列的位址。 第一個項目會接收水平框線的寬度、 第二個接收垂直框線的寬度和第三個接收矩形間框線的寬度。  
  
 *nHorz*  
 參考會接收水平框線的寬度的整數。  
  
 *nVert*  
 參考的垂直框線寬度的整數。  
  
 *nSpacing*  
 矩形間框線的寬度為整數的參考。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 這些框線會判斷控制項的外緣與控制項中包含文字的矩形之間的間距。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]  
  
##  <a name="geticon"></a>  CStatusBarCtrl::GetIcon  
 擷取目前狀態列控制項中的組件 （也稱為窗格） 圖示。  
  
```  
HICON GetIcon(int iPart) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*iPart*|組件，其中包含要擷取圖示的以零為起始的索引。 如果這個參數是-1，狀態列會假設為簡單模式下的狀態 列中。|  
  
### <a name="return-value"></a>傳回值  
 圖示的控制代碼如果方法成功，否則為 NULL。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[SB_GETICON](/windows/desktop/Controls/sb-geticon)訊息，Windows SDK 中所述。  
  
 狀態列控制項所組成的文字輸出窗格，也就是所謂的組件的資料列。 如需有關 [狀態] 列的詳細資訊，請參閱[MFC 中的狀態列實作](../../mfc/status-bar-implementation-in-mfc.md)並[設定 CStatusBarCtrl 物件的模式](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_statusBar`，也就是用來存取目前狀態列控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會將圖示複製到目前狀態列控制項的兩個窗格。 在先前章節中的程式碼範例，我們使用三個窗格建立狀態列控制項並再加入第一個窗格中的圖示。 此範例會擷取第一個窗格中的圖示，並將它新增至第二個和第三個窗格。  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]  
  
##  <a name="getparts"></a>  CStatusBarCtrl::GetParts  
 擷取狀態列控制項中的組件的計數。  
  
```  
int GetParts(
    int nParts,  
    int* pParts) const;  
```  
  
### <a name="parameters"></a>參數  
 *nParts*  
 要擷取座標的部分數目。 此參數是否大於控制項中的部分數目，訊息就會擷取現有組件的座標。  
  
 *pParts*  
 具有相同數目的項目所指定的組件數目的整數陣列中的地址*nParts*。 陣列中的每個項目會接收對應的組件的右邊緣的用戶端座標。 如果項目設定為-1，就會有該部分的右邊緣的位置延伸至右邊的 [狀態] 列中。  
  
### <a name="return-value"></a>傳回值  
 如果成功，該控制項或零，否則為中的組件數目。  
  
### <a name="remarks"></a>備註  
 此成員函式也會擷取指定的組件數目的右邊緣的座標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]  
  
##  <a name="getrect"></a>  CStatusBarCtrl::GetRect  
 擷取狀態列控制項中的組件的週框矩形。  
  
```  
BOOL GetRect(
    int nPane,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 *nPane*  
 以零為起始索引是要擷取的周框的部分。  
  
 *lpRect*  
 位址[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)接收的週框的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]  
  
##  <a name="gettext"></a>  Cstatusbarctrl:: Gettext  
 狀態列控制項的指定部分從擷取的文字。  
  
```  
CString GetText(
    int nPane,  
    int* pType = NULL) const;  
  
int GetText(
    LPCTSTR lpszText,  
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 *lpszText*  
 收到文字緩衝區的位址。 這個參數是以 null 結束的字串。  
  
 *nPane*  
 要從中擷取文字部分的以零為起始的索引。  
  
 *pType*  
 接收的類型資訊的整數指標。 類型可以是下列值之一：  
  
- **0**帶有框線，看來會低於之平面的狀態列上繪製文字。  
  
- SBT_NOBORDERS 發展無遠弗屆繪製文字。  
  
- 會出現高於之平面的 [狀態] 列框線描繪 SBT_POPOUT 文字。  
  
- SBT_OWNERDRAW 文字是否繪圖類型，SBT_OWNERDRAW *pType*接收此訊息，並傳回的文字，而不是長度和作業類型相關聯的 32 位元值。  
  
### <a name="return-value"></a>傳回值  
 以文字的字元為單位的長度，或[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含目前的文字。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]  
  
##  <a name="gettextlength"></a>  Cstatusbarctrl:: Gettextlength  
 擷取長度，以從狀態列控制項的指定部分文字的字元為單位。  
  
```  
int GetTextLength(
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 *nPane*  
 要從中擷取文字部分的以零為起始的索引。  
  
 *pType*  
 接收的類型資訊的整數指標。 類型可以是下列值之一：  
  
- **0**帶有框線，看來會低於之平面的狀態列上繪製文字。  
  
- SBT_NOBORDERS 發展無遠弗屆繪製文字。  
  
- SBT_OWNERDRAW 由父視窗來繪製文字。  
  
- 會出現高於之平面的 [狀態] 列框線描繪 SBT_POPOUT 文字。  
  
### <a name="return-value"></a>傳回值  
 以字元為單位，文字的長度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]  
  
##  <a name="gettiptext"></a>  Cstatusbarctrl:: Gettiptext  
 擷取中的狀態列窗格的工具提示文字。  
  
```  
CString GetTipText(int nPane) const;  
```  
  
### <a name="parameters"></a>參數  
 *nPane*  
 接收的工具提示文字狀態列窗格以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含要用於工具提示文字。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[SB_GETTIPTEXT](/windows/desktop/Controls/sb-gettiptext)、 Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]  
  
##  <a name="issimple"></a>  CStatusBarCtrl::IsSimple  
 檢查以判斷它是否在簡單模式下的狀態視窗控制項。  
  
```  
BOOL IsSimple() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果狀態視窗控制項為簡單模式，為非零否則為零。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[SB_ISSIMPLE](/windows/desktop/Controls/sb-issimple)、 Windows SDK 中所述。  
  
##  <a name="setbkcolor"></a>  CStatusBarCtrl::SetBkColor  
 在狀態列中設定的背景色彩。  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>參數  
 *cr*  
 COLORREF 值，指定新的背景色彩。 指定 CLR_DEFAULT 值會造成狀態列，以使用其預設背景色彩。  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](/windows/desktop/gdi/colorref)值，表示先前的預設背景色彩。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[SB_SETBKCOLOR](/windows/desktop/Controls/sb-setbkcolor)、 Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]  
  
##  <a name="seticon"></a>  CStatusBarCtrl::SetIcon  
 在狀態列中設定窗格圖示。  
  
```  
BOOL SetIcon(
    int nPane,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>參數  
 *nPane*  
 將會收到圖示 窗格的以零起始的索引。 如果此參數為-1，狀態列會假設是簡單的狀態列中。  
  
 *hIcon*  
 若要設定圖示的控制代碼。 如果這個值是 NULL，圖示會移除從組件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[SB_SETICON](/windows/desktop/Controls/sb-seticon)、 Windows SDK 中所述。  
  
### <a name="example"></a>範例  
  範例，請參閱[CStatusBarCtrl::SetBkColor](#setbkcolor)。  
  
##  <a name="setminheight"></a>  CStatusBarCtrl::SetMinHeight  
 設定狀態的最小高度列控制項的繪圖區域。  
  
```  
void SetMinHeight(int nMin);
```  
  
### <a name="parameters"></a>參數  
 *nMin*  
 最小高度，單位為像素的控制項。  
  
### <a name="remarks"></a>備註  
 最小高度是總和*nMin*和兩次的寬度，單位為像素狀態列控制項的垂直框線。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]  
  
##  <a name="setparts"></a>  CStatusBarCtrl::SetParts  
 設定組件中的狀態列控制項，而每個部分的右邊緣的座標。  
  
```  
BOOL SetParts(
    int nParts,  
    int* pWidths);
```  
  
### <a name="parameters"></a>參數  
 *nParts*  
 若要設定的部分數目。 部分數目不能大於 255。  
  
 *pWidths*  
 為所指定的組件具有相同的項目數的整數陣列中的地址*nParts*。 陣列中的每個項目會指定對應的組件的右邊緣的位置，工作區座標。 如果項目為-1，該部分的右邊緣的位置會延伸至控制項的右邊緣。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]  
  
##  <a name="setsimple"></a>  CStatusBarCtrl::SetSimple  
 指定狀態列控制項是否會顯示簡單的文字，或顯示所有先前呼叫所設定的控制項組件[SetParts](#setparts)。  
  
```  
BOOL SetSimple(BOOL bSimple = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*bSimple*  
 顯示型別旗標。 如果此參數為 TRUE 時，控制項就會顯示簡單的文字;如果是 FALSE，它會顯示多個部分。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
 如果您的應用程式會從非簡單變更狀態列控制項為 simple 時，或反之亦然，系統立即重繪控制項。  
  
##  <a name="settext"></a>  CStatusBarCtrl::SetText  
 在狀態列控制項的指定部分設定文字。  
  
```  
BOOL SetText(
    LPCTSTR lpszText,  
    int nPane,  
    int nType);
```  
  
### <a name="parameters"></a>參數  
 *lpszText*  
 以 Null 結束的字串位址，其指定要設定的文字。 如果*n*是 SBT_OWNERDRAW， *lpszText*代表 32 位元的資料。  
  
 *nPane*  
 要設定之部分的以零為起始的索引。 如果此值為 255，則假設狀態列控制項是只有一個部分的簡單控制項。  
  
 *n*  
 繪圖作業的類型。 請參閱[SB_SETTEXT 訊息](/windows/desktop/Controls/sb-settext)取得一份可能的值。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 已變更，使其在控制項接著接收 WM_PAINT 訊息時，顯示新的文字的控制項部分失效的訊息。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]  
  
##  <a name="settiptext"></a>  Cstatusbarctrl:: Settiptext  
 設定工具提示文字窗格的 [狀態] 列中。  
  
```  
void SetTipText(
    int nPane,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>參數  
 *nPane*  
 接收的工具提示文字狀態列窗格以零為起始的索引。  
  
 *pszTipText*  
 包含的工具提示文字的字串指標。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[SB_SETTIPTEXT](/windows/desktop/Controls/sb-settiptext)、 Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl 類別](../../mfc/reference/ctoolbarctrl-class.md)
