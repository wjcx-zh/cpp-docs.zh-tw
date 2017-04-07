---
title: "CStatusBarCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- Windows common controls [C++], CStatusBarCtrl
- CStatusBarCtrl class
- status bar controls
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
caps.latest.revision: 20
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 619fb88b96f60ab2dc0911cb8ea0b66574ea4287
ms.lasthandoff: 02/24/2017

---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl 類別
提供 Windows 通用狀態列控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CStatusBarCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|建構 `CStatusBarCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CStatusBarCtrl::Create](#create)|建立狀態列控制項並將它附加`CStatusBarCtrl`物件。|  
|[CStatusBarCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立狀態列控制項，並附加至該`CStatusBarCtrl`物件。|  
|[CStatusBarCtrl::DrawItem](#drawitem)|主控描繪狀態列控制項會變更的視覺外觀時呼叫。|  
|[CStatusBarCtrl::GetBorders](#getborders)|擷取目前狀態列控制項的水平和垂直框線的寬度。|  
|[CStatusBarCtrl::GetIcon](#geticon)|擷取目前狀態列控制項中的組件 （也稱為窗格） 圖示。|  
|[CStatusBarCtrl::GetParts](#getparts)|抓取狀態列控制項中的組件的計數。|  
|[CStatusBarCtrl::GetRect](#getrect)|擷取週框的狀態列控制項中的組件。|  
|[CStatusBarCtrl::GetText](#gettext)|從一個狀態列控制項的指定部分擷取的文字。|  
|[CStatusBarCtrl::GetTextLength](#gettextlength)|擷取的長度，以字元為單位，從一個狀態列控制項的指定部分的文字。|  
|[Cstatusbarctrl:: Gettiptext](#gettiptext)|擷取在狀態列窗格的工具提示文字。|  
|[CStatusBarCtrl::IsSimple](#issimple)|檢查以判斷它是否在簡單模式下狀態視窗控制項。|  
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|在狀態列中設定的背景色彩。|  
|[CStatusBarCtrl::SetIcon](#seticon)|在狀態列中設定窗格中的圖示。|  
|[CStatusBarCtrl::SetMinHeight](#setminheight)|設定狀態的最小高度列控制項的繪圖區域。|  
|[CStatusBarCtrl::SetParts](#setparts)|在狀態列控制項和每個部分的右邊緣的座標中設定部分的數目。|  
|[CStatusBarCtrl::SetSimple](#setsimple)|指定狀態列控制項是否會顯示簡單的文字，則顯示所有先前呼叫所設定的控制項組件`SetParts`。|  
|[CStatusBarCtrl::SetText](#settext)|在狀態列控制項的指定部分設定文字。|  
|[Cstatusbarctrl:: Settiptext](#settiptext)|在狀態列中設定一個窗格的工具提示文字。|  
  
## <a name="remarks"></a>備註  
 「 狀態列控制項 」 是水平視窗，通常會顯示在父視窗，在其中應用程式可以顯示各種狀態資訊的底部。 狀態列控制項可以分割成組件來顯示多個類型的資訊。  
  
 這個控制項 (並因此`CStatusBarCtrl`類別) 僅適用於執行 Windows 95/98 和 Windows NT 版本 3.51 下的程式和更新版本。  
  
 如需有關使用`CStatusBarCtrl`，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatusBarCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="create"></a>CStatusBarCtrl::Create  
 建立狀態列控制項並將它附加`CStatusBarCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定狀態列控制項的樣式。 套用狀態列控制項樣式中列出的任何結合[常用的控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775498)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 這個參數必須包含**WS_CHILD**樣式。 它也應該包含**WS_VISIBLE**樣式。  
  
 `rect`  
 指定狀態列控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
 `pParentWnd`  
 指定狀態列控制項的父視窗，通常`CDialog`。 它不得為**NULL。**  
  
 `nID`  
 指定狀態列控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 您建構`CStatusBarCtrl`兩個步驟。 首先，呼叫建構函式，並接著呼叫**建立**，其建立狀態列控制項，並將它附加`CStatusBarCtrl`物件。  
  
 狀態視窗的預設位置是父視窗的底部，但是您可以指定`CCS_TOP`樣式讓它出現在父視窗工作區頂端。 您可以指定**SBARS_SIZEGRIP**包含狀態視窗右端的調整大小底框樣式。 結合`CCS_TOP`和**SBARS_SIZEGRIP**不建議樣式，因為產生的調整大小底框沒有正常運作，即使系統則會在狀態視窗中繪製它。  
  
 若要建立狀態列上具有延伸的視窗樣式，請呼叫[CStatusBarCtrl::CreateEx](#createex)而不是**建立**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&1;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>CStatusBarCtrl::CreateEx  
 建立控制項 （子視窗），並將它與相關聯`CStatusBarCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwExStyle`  
 指定正在建立的控制項的延伸的樣式。 如需延伸視窗樣式，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定狀態列控制項的樣式。 套用狀態列控制項樣式中列出的任何結合[常用的控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775498)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 這個參數必須包含**WS_CHILD**樣式。 它也應該包含**WS_VISIBLE**樣式。  
  
 `rect`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立、 用戶端座標中的視窗的`pParentWnd`。  
  
 `pParentWnd`  
 是控制項的父視窗的指標。  
  
 `nID`  
 控制項的子視窗的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是[建立](#create)套用延伸的視窗樣式，指定 Windows 延伸的樣式序言**WS_EX_**。  
  
##  <a name="cstatusbarctrl"></a>CStatusBarCtrl::CStatusBarCtrl  
 建構 `CStatusBarCtrl` 物件。  
  
```  
CStatusBarCtrl();
```  
  
##  <a name="drawitem"></a>CStatusBarCtrl::DrawItem  
 當主控描繪狀態列控制項會變更的視覺外觀的架構所呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDrawItemStruct`  
 長指標[DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802)結構，其中包含所需的繪圖的類型資訊。  
  
### <a name="remarks"></a>備註  
 **ItemAction**成員`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。  
  
 根據預設，此成員函式沒有作用。 覆寫此成員函式實作繪圖的主控描繪`CStatusBarCtrl`物件。  
  
 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件`lpDrawItemStruct`之前此成員函式會結束。  
  
##  <a name="getborders"></a>CStatusBarCtrl::GetBorders  
 擷取目前狀態列控制項的寬度水平及垂直框線和矩形之間的間距。  
  
```  
BOOL GetBorders(int* pBorders) const;  
  
BOOL GetBorders(
    int& nHorz,  
    int& nVert,  
    int& nSpacing) const;  
```  
  
### <a name="parameters"></a>參數  
 *pBorders*  
 具有三個元素的整數陣列的位址。 第一個項目接收水平框線的寬度，第二個接收垂直框線的寬度，第三個接收矩形間框線的寬度。  
  
 *nHorz*  
 接收的水平框線寬度的整數的參考。  
  
 *轉換*  
 接收的垂直框線寬度的整數的參考。  
  
 *nSpacing*  
 接收的矩形間框線寬度的整數的參考。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 這些框線判斷控制項的邊緣和控制項中包含文字的矩形之間的間距。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&2;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]  
  
##  <a name="geticon"></a>CStatusBarCtrl::GetIcon  
 擷取目前狀態列控制項中的組件 （也稱為窗格） 圖示。  
  
```  
HICON GetIcon(int iPart) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iPart`|組件，其中包含要擷取圖示的以零為起始的索引。 如果這個參數是-1，狀態列會假設為簡單模式狀態列。|  
  
### <a name="return-value"></a>傳回值  
 圖示的控制代碼如果方法成功。否則， `NULL`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[SB_GETICON](http://msdn.microsoft.com/library/windows/desktop/bb760744)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 狀態列控制項的資料列文字輸出窗格，也就是個部分所組成。 如需 [狀態] 列的詳細資訊，請參閱[MFC 中的狀態列實作](../../mfc/status-bar-implementation-in-mfc.md)和[設定 CStatusBarCtrl 物件的模式](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_statusBar`，也就是用來存取目前狀態列控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會將圖示複製到目前狀態列控制項的兩個窗格。 在先前章節中的程式碼範例我們建立一個狀態列控制項具有三個窗格，然後再新增至第一個窗格的 圖示。 這個範例會擷取第一個窗格中的圖示，並將它新增至第二個和第三個窗格。  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]  
  
##  <a name="getparts"></a>CStatusBarCtrl::GetParts  
 抓取狀態列控制項中的組件的計數。  
  
```  
int GetParts(
    int nParts,  
    int* pParts) const;  
```  
  
### <a name="parameters"></a>參數  
 `nParts`  
 要擷取座標的部分數目。 如果控制項中的部分數目大於此參數，將訊息擷取現有組件的座標。  
  
 *pParts*  
 具有相同數目的項目所指定的組件數目的整數陣列的位址`nParts`。 陣列中的每個項目會接收對應的組件的右邊緣的座標。 如果項目設定為 – 1，狀態列的右邊緣來擴充該部分的右邊緣的位置。  
  
### <a name="return-value"></a>傳回值  
 在控制項中，如果成功或零，否則為組件數目。  
  
### <a name="remarks"></a>備註  
 此成員函式也會擷取指定數目的組件的右邊緣的座標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&3;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]  
  
##  <a name="getrect"></a>CStatusBarCtrl::GetRect  
 擷取週框的狀態列控制項中的組件。  
  
```  
BOOL GetRect(
    int nPane,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `nPane`  
 部分的周框矩形是要擷取的以零為起始的索引。  
  
 `lpRect`  
 位址[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)接收，這個周框的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&4;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]  
  
##  <a name="gettext"></a>CStatusBarCtrl::GetText  
 從一個狀態列控制項的指定部分擷取的文字。  
  
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
 `lpszText`  
 接收文字緩衝區的位址。 這個參數是以 null 結束的字串。  
  
 `nPane`  
 要從中擷取文字部分的以零為起始的索引。  
  
 `pType`  
 收到的型別資訊的整數指標。 類型可以是下列值之一︰  
  
- **0**出現低於狀態列面板的框線繪製文字。  
  
- `SBT_NOBORDERS`無國界繪製文字。  
  
- `SBT_POPOUT`繪製文字顯示高於狀態列面板的框線。  
  
- `SBT_OWNERDRAW`如果文字具有`SBT_OWNERDRAW`繪圖類型，`pType`接收此訊息，並傳回的文字，而不是長度和作業類型相關聯的 32 位元值。  
  
### <a name="return-value"></a>傳回值  
 以文字的字元為單位的長度或[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含目前的文字。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&5;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]  
  
##  <a name="gettextlength"></a>CStatusBarCtrl::GetTextLength  
 擷取長度，以字元為單位，從一個狀態列控制項的指定部分的文字。  
  
```  
int GetTextLength(
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 `nPane`  
 要從中擷取文字部分的以零為起始的索引。  
  
 `pType`  
 收到的型別資訊的整數指標。 類型可以是下列值之一︰  
  
- **0**出現低於狀態列面板的框線繪製文字。  
  
- `SBT_NOBORDERS`無國界繪製文字。  
  
- `SBT_OWNERDRAW`繪製文字是由父視窗。  
  
- `SBT_POPOUT`繪製文字顯示高於狀態列面板的框線。  
  
### <a name="return-value"></a>傳回值  
 以字元為單位，文字的長度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&6;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]  
  
##  <a name="gettiptext"></a>Cstatusbarctrl:: Gettiptext  
 擷取在狀態列窗格的工具提示文字。  
  
```  
CString GetTipText(int nPane) const;  
```  
  
### <a name="parameters"></a>參數  
 `nPane`  
 用於接收工具提示文字狀態列窗格的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含要用於工具提示文字。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[SB_GETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760751)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&7;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]  
  
##  <a name="issimple"></a>CStatusBarCtrl::IsSimple  
 檢查以判斷它是否在簡單模式下狀態視窗控制項。  
  
```  
BOOL IsSimple() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果是簡單的模式，狀態視窗控制項為非零否則為零。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[SB_ISSIMPLE](http://msdn.microsoft.com/library/windows/desktop/bb760753)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setbkcolor"></a>CStatusBarCtrl::SetBkColor  
 在狀態列中設定的背景色彩。  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>參數  
 `cr`  
 **COLORREF**值，指定新的背景色彩。 指定`CLR_DEFAULT`值，讓狀態列，以使用其預設背景色彩。  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，表示先前的預設背景色彩。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[SB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760754)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&8;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]  
  
##  <a name="seticon"></a>CStatusBarCtrl::SetIcon  
 在狀態列中設定窗格中的圖示。  
  
```  
BOOL SetIcon(
    int nPane,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>參數  
 `nPane`  
 將會收到圖示 窗格的以零起始的索引。 如果這個參數是-1，狀態列會假設為簡單的狀態列。  
  
 `hIcon`  
 設定圖示的控制代碼。 如果這個值是**NULL**，圖示會移除從組件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[SB_SETICON](http://msdn.microsoft.com/library/windows/desktop/bb760755)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CStatusBarCtrl::SetBkColor](#setbkcolor)。  
  
##  <a name="setminheight"></a>CStatusBarCtrl::SetMinHeight  
 設定狀態的最小高度列控制項的繪圖區域。  
  
```  
void SetMinHeight(int nMin);
```  
  
### <a name="parameters"></a>參數  
 `nMin`  
 最小高度，單位為像素控制項。  
  
### <a name="remarks"></a>備註  
 最小高度是總和`nMin`和兩次的寬度，單位為像素狀態列控制項的垂直框線。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&9;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]  
  
##  <a name="setparts"></a>CStatusBarCtrl::SetParts  
 在狀態列控制項和每個部分的右邊緣的座標中設定部分的數目。  
  
```  
BOOL SetParts(
    int nParts,  
    int* pWidths);
```  
  
### <a name="parameters"></a>參數  
 `nParts`  
 若要設定的部分數目。 部分數目不能大於 255。  
  
 *pWidths*  
 為所指定的組件具有相同的項目數的整數陣列的位址`nParts`。 陣列中每個項目會指定對應的組件的右邊緣的位置，用戶端座標中。 如果項目是 – 1，該部分的右邊緣的位置會延伸到控制項的右邊緣。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&10;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]  
  
##  <a name="setsimple"></a>CStatusBarCtrl::SetSimple  
 指定狀態列控制項是否會顯示簡單的文字，則顯示所有先前呼叫所設定的控制項組件[SetParts](#setparts)。  
  
```  
BOOL SetSimple(BOOL bSimple = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bSimple`  
 顯示類型的旗標。 如果這個參數是`TRUE`，控制項會顯示簡單的文字; 如果是`FALSE`，它會顯示多個組件。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
 如果您的應用程式會從非簡單變更狀態列控制項為 simple 時，或反之亦然，系統立即重繪控制項。  
  
##  <a name="settext"></a>CStatusBarCtrl::SetText  
 在狀態列控制項的指定部分設定文字。  
  
```  
BOOL SetText(
    LPCTSTR lpszText,  
    int nPane,  
    int nType);
```  
  
### <a name="parameters"></a>參數  
 `lpszText`  
 以 Null 結束的字串位址，其指定要設定的文字。 如果 `nType` 為 `SBT_OWNERDRAW``lpszText` 代表 32 位元的資料。  
  
 `nPane`  
 要設定之部分的以零為起始的索引。 如果此值為 255，則假設狀態列控制項是只有一個部分的簡單控制項。  
  
 `nType`  
 繪圖作業的類型。 請參閱[SB_SETTEXT 訊息](http://msdn.microsoft.com/library/bb760758\(vs.85\).aspx)的可能值的清單。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 此訊息會使已變更的控制項部分失效，使其在控制項接著接收 `WM_PAINT` 訊息時顯示新的文字。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&11;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]  
  
##  <a name="settiptext"></a>Cstatusbarctrl:: Settiptext  
 在狀態列中設定一個窗格的工具提示文字。  
  
```  
void SetTipText(
    int nPane,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>參數  
 `nPane`  
 用於接收工具提示文字狀態列窗格的以零為起始的索引。  
  
 *pszTipText*  
 包含的工具提示文字的字串指標。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[SB_SETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760759)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CStatusBarCtrl #&12;](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl 類別](../../mfc/reference/ctoolbarctrl-class.md)

