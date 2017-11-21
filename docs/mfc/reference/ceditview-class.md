---
title: "CEditView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEditView
- AFXEXT/CEditView
- AFXEXT/CEditView::CEditView
- AFXEXT/CEditView::FindText
- AFXEXT/CEditView::GetBufferLength
- AFXEXT/CEditView::GetEditCtrl
- AFXEXT/CEditView::GetPrinterFont
- AFXEXT/CEditView::GetSelectedText
- AFXEXT/CEditView::LockBuffer
- AFXEXT/CEditView::PrintInsideRect
- AFXEXT/CEditView::SerializeRaw
- AFXEXT/CEditView::SetPrinterFont
- AFXEXT/CEditView::SetTabStops
- AFXEXT/CEditView::UnlockBuffer
- AFXEXT/CEditView::OnFindNext
- AFXEXT/CEditView::OnReplaceAll
- AFXEXT/CEditView::OnReplaceSel
- AFXEXT/CEditView::OnTextNotFound
- AFXEXT/CEditView::dwStyleDefault
dev_langs: C++
helpviewer_keywords:
- CEditView [MFC], CEditView
- CEditView [MFC], FindText
- CEditView [MFC], GetBufferLength
- CEditView [MFC], GetEditCtrl
- CEditView [MFC], GetPrinterFont
- CEditView [MFC], GetSelectedText
- CEditView [MFC], LockBuffer
- CEditView [MFC], PrintInsideRect
- CEditView [MFC], SerializeRaw
- CEditView [MFC], SetPrinterFont
- CEditView [MFC], SetTabStops
- CEditView [MFC], UnlockBuffer
- CEditView [MFC], OnFindNext
- CEditView [MFC], OnReplaceAll
- CEditView [MFC], OnReplaceSel
- CEditView [MFC], OnTextNotFound
- CEditView [MFC], dwStyleDefault
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 38b8389418657499d43263399f1a05b3a0326c84
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ceditview-class"></a>CEditView 類別
檢視類別的類型，這個類型提供 Windows 編輯控制項功能，而且可用於實作簡單的文字編輯器功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CEditView : public CCtrlView  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CEditView::CEditView](#ceditview)|建構類型 `CEditView` 的物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CEditView::FindText](#findtext)|搜尋文字內的字串。|  
|[CEditView::GetBufferLength](#getbufferlength)|取得字元緩衝區的長度。|  
|[CEditView::GetEditCtrl](#geteditctrl)|提供存取`CEdit`部分`CEditView`（Windows 編輯控制項） 的物件。|  
|[CEditView::GetPrinterFont](#getprinterfont)|擷取目前的印表機字型。|  
|[CEditView::GetSelectedText](#getselectedtext)|擷取目前文字選取範圍。|  
|[CEditView::LockBuffer](#lockbuffer)|鎖定緩衝區。|  
|[CEditView::PrintInsideRect](#printinsiderect)|呈現指定的矩形內的文字。|  
|[CEditView::SerializeRaw](#serializeraw)|將序列化`CEditView`未經處理文字與磁碟的物件。|  
|[CEditView::SetPrinterFont](#setprinterfont)|將新的印表機字型設定。|  
|[CEditView::SetTabStops](#settabstops)|設定定位停駐點的螢幕顯示和列印。|  
|[CEditView::UnlockBuffer](#unlockbuffer)|解除鎖定緩衝區。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CEditView::OnFindNext](#onfindnext)|尋找下一個出現的文字字串。|  
|[CEditView::OnReplaceAll](#onreplaceall)|新字串，取代所有出現的指定字串。|  
|[CEditView::OnReplaceSel](#onreplacesel)|取代目前選取範圍。|  
|[CEditView::OnTextNotFound](#ontextnotfound)|比對任何其他文字的尋找作業失敗時呼叫。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CEditView::dwStyleDefault](#dwstyledefault)|預設型別物件的樣式**CEditView。**|  
  
## <a name="remarks"></a>備註  
 `CEditView`類別會提供下列額外的函數：  
  
-   列印。  
  
-   尋找和取代。  
  
 因為類別`CEditView`類別衍生`CView`，類別的物件`CEditView`可以搭配文件和文件範本。  
  
 每個`CEditView`控制項的文字就會保留在它自己的全域記憶體物件。 您的應用程式可以有任意數目的`CEditView`物件。  
  
 建立類型的物件`CEditView`如果您想編輯視窗與上面所列的新增功能，或您想要簡單的文字編輯器功能。 A`CEditView`物件可以佔用整個視窗的工作區。 衍生您自己的類別從`CEditView`加入或修改基本的功能，或宣告可以加入至文件範本的類別。  
  
 類別的預設實作`CEditView`處理下列命令： **ID_EDIT_SELECT_ALL**， **ID_EDIT_FIND**， **ID_EDIT_REPLACE**， **ID_EDIT_REPEAT**，和**ID_FILE_PRINT**。  
  
 預設字元限制`CEditView`是 (1024年\*1024年-1 = 1048575)。 這可以藉由呼叫變更**EM_LIMITTEXT**基礎函式編輯控制項。 不過，限制會根據作業系統而不同，而且類型的編輯控制項 （單一或多行）。 如需有關這些限制的詳細資訊，請參閱[EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607)。  
  
 若要變更這項限制在控制項中的，覆寫`OnCreate()`函式您`CEditView`類別，並插入下列程式碼行：  
  
 [!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]  
  
 類型的物件`CEditView`(或從衍生型別的`CEditView`) 具有下列限制：  
  
- `CEditView`未實作 true 所見即所得 (WYSIWYG) 編輯。 在螢幕上的可讀性和比對的列印的輸出之間沒有選擇`CEditView`且螢幕閱讀。  
  
- `CEditView`可以在單一字型顯示文字。 未將特殊字元格式支援。 請參閱類別[CRichEditView](../../mfc/reference/cricheditview-class.md)更高的功能。  
  
-   文字數量`CEditView`可包含限制。 限制是一樣`CEdit`控制項。  
  
 如需有關`CEditView`，請參閱[衍生檢視類別中可用 MFC](../../mfc/derived-view-classes-available-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CEditView`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxext.h  
  
##  <a name="ceditview"></a>CEditView::CEditView  
 建構類型 `CEditView` 的物件。  
  
```  
CEditView();
```  
  
### <a name="remarks"></a>備註  
 之後建構物件，您必須呼叫[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)函式使用編輯控制項之前。 如果您是衍生自`CEditView`並將它加入至範本使用`CWinApp::AddDocTemplate`，架構會呼叫這兩個建構函式和**建立**函式。  
  
##  <a name="dwstyledefault"></a>CEditView::dwStyleDefault  
 包含的預設樣式`CEditView`物件。  
  
```  
static const DWORD dwStyleDefault;  
```  
  
### <a name="remarks"></a>備註  
 傳遞做為這個靜態成員`dwStyle`參數**建立**函數來取得的預設樣式`CEditView`物件。  
  
##  <a name="findtext"></a>CEditView::FindText  
 呼叫`FindText`函式來搜尋`CEditView`物件的文字緩衝區。  
  
```  
BOOL FindText(
    LPCTSTR lpszFind,  
    BOOL bNext = TRUE,  
    BOOL bCase = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `lpszFind`  
 要找的文字。  
  
 `bNext`  
 指定搜尋方向。 如果**TRUE**，搜尋方向是往緩衝區的結尾。 如果**FALSE**，搜尋方向是從緩衝區開頭。  
  
 `bCase`  
 指定搜尋是否區分大小寫。 如果**TRUE**，搜尋不區分大小寫。 如果**FALSE**，搜尋不區分大小寫。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果找到搜尋文字否則便是 0。  
  
### <a name="remarks"></a>備註  
 此函式所指定的文字的緩衝區中搜尋文字`lpszFind`開始所指定的方向中的目前選取範圍， `bNext`，與所指定的區分大小寫`bCase`。 如果找到文字，它將選取項目設定為找到的文字，並傳回非零值。 如果找不到文字，則函數會傳回 0。  
  
 您通常不需要呼叫`FindText`作用，除非您覆寫`OnFindNext`，而它會呼叫`FindText`。  
  
##  <a name="getbufferlength"></a>CEditView::GetBufferLength  
 呼叫此成員函式可取得目前在編輯控制項的緩衝區，不包括 null 結束字元的字元數。  
  
```  
UINT GetBufferLength() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在緩衝區中字串的長度。  
  
##  <a name="geteditctrl"></a>CEditView::GetEditCtrl  
 呼叫`GetEditCtrl`取得編輯檢視所使用之編輯控制項的參考。  
  
```  
CEdit& GetEditCtrl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 對 `CEdit` 物件的參考。  
  
### <a name="remarks"></a>備註  
 此控制項的類型是[CEdit](../../mfc/reference/cedit-class.md)，因此您可以使用操作直接使用 Windows 編輯控制項`CEdit`成員函式。  
  
> [!CAUTION]
>  使用`CEdit`物件變更狀態的基礎 Windows 編輯控制項。 例如，您不應該變更使用的索引標籤上設定[CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops)運作，因為`CEditView`快取以供編輯控制項中或在列印中的這些設定。 請改用[CEditView::SetTabStops](#settabstops)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]  
  
##  <a name="getprinterfont"></a>CEditView::GetPrinterFont  
 呼叫`GetPrinterFont`取得指標[CFont](../../mfc/reference/cfont-class.md)物件，描述目前印表機字型。  
  
```  
CFont* GetPrinterFont() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`CFont`物件，指定目前的印表機字型。**NULL**如果尚未設定印表機字型。 該指標可能是暫時性的，因此不應該儲存供日後使用。  
  
### <a name="remarks"></a>備註  
 如果印表機字型尚未設定，列印的行為預設`CEditView`類別是要使用的相同字型來顯示列印。  
  
 您可以使用此函式來判斷目前的印表機字型。 如果不想要的印表機字型，請使用[CEditView::SetPrinterFont](#setprinterfont)加以變更。  
  
##  <a name="getselectedtext"></a>CEditView::GetSelectedText  
 呼叫`GetSelectedText`複製到選取的文字`CString`物件，最多的選取範圍或選取範圍中之前的第一個歸位字元的字元結尾。  
  
```  
void GetSelectedText(CString& strResult) const;  
```  
  
### <a name="parameters"></a>參數  
 `strResult`  
 若要參考`CString`要接收所選取的文字的物件。  
  
##  <a name="lockbuffer"></a>CEditView::LockBuffer  
 呼叫此成員函式可取得緩衝區的指標。 不應該修改的緩衝區。  
  
```  
LPCTSTR LockBuffer() const;  
```  
  
### <a name="return-value"></a>傳回值  
 編輯控制項的緩衝區的指標。  
  
##  <a name="onfindnext"></a>CEditView::OnFindNext  
 搜尋的文字搜尋中所指定的文字的緩衝區`lpszFind`，所指定的方向`bNext`，與所指定的區分大小寫`bCase`。  
  
```  
virtual void OnFindNext(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>參數  
 `lpszFind`  
 要找的文字。  
  
 `bNext`  
 指定搜尋方向。 如果**TRUE**，搜尋方向是往緩衝區的結尾。 如果**FALSE**，搜尋方向是從緩衝區開頭。  
  
 `bCase`  
 指定搜尋是否區分大小寫。 如果**TRUE**，搜尋不區分大小寫。 如果**FALSE**，搜尋不區分大小寫。  
  
### <a name="remarks"></a>備註  
 搜尋會從目前的選取範圍的開頭，並透過呼叫來完成[FindText](#findtext)。 在預設實作中，`OnFindNext`呼叫[OnTextNotFound](#ontextnotfound)如果找不到文字。  
  
 覆寫`OnFindNext`變更方式`CEditView`-衍生的物件搜尋的文字。 `CEditView`呼叫`OnFindNext`當使用者在標準的 [尋找] 對話方塊中選擇 [尋找下一個] 按鈕。  
  
##  <a name="onreplaceall"></a>CEditView::OnReplaceAll  
 `CEditView`呼叫`OnReplaceAll`當使用者在標準的 [取代] 對話方塊中選取 [全部取代] 按鈕。  
  
```  
virtual void OnReplaceAll(
    LPCTSTR lpszFind,  
    LPCTSTR lpszReplace,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>參數  
 `lpszFind`  
 要找的文字。  
  
 `lpszReplace`  
 要取代搜尋文字的文字。  
  
 `bCase`  
 指定搜尋是否區分大小寫。 如果**TRUE**，搜尋不區分大小寫。 如果**FALSE**，搜尋不區分大小寫。  
  
### <a name="remarks"></a>備註  
 `OnReplaceAll`搜尋的文字搜尋中所指定的文字的緩衝區`lpszFind`，與所指定的區分大小寫`bCase`。 搜尋會從目前的選取範圍的開頭。 每次找到搜尋文字時，此函式取代該文字項目所指定的文字`lpszReplace`。 搜尋透過呼叫來完成[FindText](#findtext)。 在預設實作中， [OnTextNotFound](#ontextnotfound)如果找不到文字，則呼叫。  
  
 如果不符合目前的選取範圍`lpszFind`，選取項目已更新為所指定之文字的第一個出現`lpszFind`而且不會執行取代。 這可讓使用者確認這是他們想要執行選取項目不符合所要取代的文字時。  
  
 覆寫`OnReplaceAll`變更方式`CEditView`-衍生的物件取代文字。  
  
##  <a name="onreplacesel"></a>CEditView::OnReplaceSel  
 `CEditView`呼叫`OnReplaceSel`當使用者在標準的 [取代] 對話方塊中選取 [取代] 按鈕。  
  
```  
virtual void OnReplaceSel(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    LPCTSTR lpszReplace);
```  
  
### <a name="parameters"></a>參數  
 `lpszFind`  
 要找的文字。  
  
 `bNext`  
 指定搜尋方向。 如果**TRUE**，搜尋方向是往緩衝區的結尾。 如果**FALSE**，搜尋方向是從緩衝區開頭。  
  
 `bCase`  
 指定搜尋是否區分大小寫。 如果**TRUE**，搜尋不區分大小寫。 如果**FALSE**，搜尋不區分大小寫。  
  
 `lpszReplace`  
 要取代找到的文字的文字。  
  
### <a name="remarks"></a>備註  
 此函式之後取代選取範圍，所指定的文字的下一個相符項目緩衝區中搜尋文字`lpszFind`，所指定的方向`bNext`，與所指定的區分大小寫`bCase`。 搜尋透過呼叫來完成[FindText](#findtext)。 如果找不到文字， [OnTextNotFound](#ontextnotfound)呼叫。  
  
 覆寫`OnReplaceSel`變更方式`CEditView`-衍生的物件取代選取的文字。  
  
##  <a name="ontextnotfound"></a>CEditView::OnTextNotFound  
 若要變更預設實作中，Windows 函式會呼叫此函式會覆寫**MessageBeep**。  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>參數  
 `lpszFind`  
 要找的文字。  
  
##  <a name="printinsiderect"></a>CEditView::PrintInsideRect  
 呼叫`PrintInsideRect`列印文字中所指定的矩形*rectLayout*。  
  
```  
UINT PrintInsideRect(
    CDC *pDC,  
    RECT& rectLayout,  
    UINT nIndexStart,  
    UINT nIndexStop);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 印表機裝置內容的指標。  
  
 *rectLayout*  
 若要參考[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT 結構](../../mfc/reference/rect-structure1.md)指定文字為呈現的矩形。  
  
 `nIndexStart`  
 要轉譯的第一個字元的緩衝區內的索引。  
  
 `nIndexStop`  
 後面要呈現的最後一個字元的字元緩衝區中的索引。  
  
### <a name="return-value"></a>傳回值  
 為要列印的下一個字元的索引 （也就是說，之後呈現的最後一個字元的字元）。  
  
### <a name="remarks"></a>備註  
 如果`CEditView`控制項沒有樣式**ES_AUTOHSCROLL**，文字換行呈現矩形內。 如果控制項沒有樣式**ES_AUTOHSCROLL**，文字會被裁剪矩形的右邊緣。  
  
 **Rect.bottom**元素*rectLayout*物件已變更，因此矩形的維度定義的部分原始文字所佔據的矩形。  
  
##  <a name="serializeraw"></a>CEditView::SerializeRaw  
 呼叫`SerializeRaw`有`CArchive`物件讀取或寫入文字`CEditView`物件至文字檔案。  
  
```  
void SerializeRaw(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 `ar`  
 若要參考`CArchive`序列化將文字儲存到的物件。  
  
### <a name="remarks"></a>備註  
 `SerializeRaw`不同於`CEditView`的內部實作`Serialize`在於它讀取和寫入的文字，而不前置物件描述的資料。  
  
##  <a name="setprinterfont"></a>CEditView::SetPrinterFont  
 呼叫`SetPrinterFont`設為所指定之字型的印表機字型`pFont`。  
  
```  
void SetPrinterFont(CFont* pFont);
```  
  
### <a name="parameters"></a>參數  
 `pFont`  
 類型的物件的指標`CFont`。 如果**NULL**，用於列印的字型為基礎的字型。  
  
### <a name="remarks"></a>備註  
 如果您想要一律使用特定字型列印檢視，包括呼叫`SetPrinterFont`在您的類別`OnPreparePrinting`函式。 此虛擬函式稱為在列印之前，讓字型變更之前，會列印檢視的內容。  
  
##  <a name="settabstops"></a>CEditView::SetTabStops  
 呼叫此函式可設定定位停駐點的顯示和列印使用。  
  
```  
void SetTabStops(int nTabStops);
```  
  
### <a name="parameters"></a>參數  
 `nTabStops`  
 對話方塊單位的每個定位停駐點的寬度。  
  
### <a name="remarks"></a>備註  
 支援單一定位點寬度。 (`CEdit`物件支援多個定位點寬度。)寬度會以對話方塊單位等於 4 的平均字元寬度 （根據大寫和小寫字母字元只） 在列印或顯示時所使用的字型。 您不應該使用`CEdit::SetTabStops`因為`CEditView`必須快取的定位停駐點的值。  
  
 此函式會修改它會呼叫的物件的索引標籤。 若要變更索引標籤停止每個`CEditView`物件在您的應用程式中，呼叫每個物件的`SetTabStops`函式。  
  
### <a name="example"></a>範例  
 此程式碼片段中每個第四個字元的控制項設定定位停駐點，藉由仔細測量控制項所使用的字型。  
  
 [!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]  
  
##  <a name="unlockbuffer"></a>CEditView::UnlockBuffer  
 呼叫此成員函式可解除鎖定緩衝區。  
  
```  
void UnlockBuffer() const;  
```  
  
### <a name="remarks"></a>備註  
 呼叫`UnlockBuffer`完成使用所傳回的指標之後[LockBuffer](#lockbuffer)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 SUPERPAD](../../visual-cpp-samples.md)   
 [CCtrlView 類別](../../mfc/reference/cctrlview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CEdit 類別](../../mfc/reference/cedit-class.md)   
 [CDocument 類別](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)   
 [CCtrlView 類別](../../mfc/reference/cctrlview-class.md)   
 [CRichEditView 類別](../../mfc/reference/cricheditview-class.md)
