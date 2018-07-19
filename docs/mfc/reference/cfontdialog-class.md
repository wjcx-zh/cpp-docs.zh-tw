---
title: CFontDialog 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFontDialog
- AFXDLGS/CFontDialog
- AFXDLGS/CFontDialog::CFontDialog
- AFXDLGS/CFontDialog::DoModal
- AFXDLGS/CFontDialog::GetCharFormat
- AFXDLGS/CFontDialog::GetColor
- AFXDLGS/CFontDialog::GetCurrentFont
- AFXDLGS/CFontDialog::GetFaceName
- AFXDLGS/CFontDialog::GetSize
- AFXDLGS/CFontDialog::GetStyleName
- AFXDLGS/CFontDialog::GetWeight
- AFXDLGS/CFontDialog::IsBold
- AFXDLGS/CFontDialog::IsItalic
- AFXDLGS/CFontDialog::IsStrikeOut
- AFXDLGS/CFontDialog::IsUnderline
- AFXDLGS/CFontDialog::m_cf
dev_langs:
- C++
helpviewer_keywords:
- CFontDialog [MFC], CFontDialog
- CFontDialog [MFC], DoModal
- CFontDialog [MFC], GetCharFormat
- CFontDialog [MFC], GetColor
- CFontDialog [MFC], GetCurrentFont
- CFontDialog [MFC], GetFaceName
- CFontDialog [MFC], GetSize
- CFontDialog [MFC], GetStyleName
- CFontDialog [MFC], GetWeight
- CFontDialog [MFC], IsBold
- CFontDialog [MFC], IsItalic
- CFontDialog [MFC], IsStrikeOut
- CFontDialog [MFC], IsUnderline
- CFontDialog [MFC], m_cf
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b7f82988e8756a6894464c9d95ae47fe6baf922
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336809"
---
# <a name="cfontdialog-class"></a>CFontDialog 類別
可讓您將字型選取對話方塊中併入您的應用程式。  
  
## <a name="syntax"></a>語法  
  
```  
class CFontDialog : public CCommonDialog  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CFontDialog::CFontDialog](#cfontdialog)|建構 `CFontDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CFontDialog::DoModal](#domodal)|會顯示對話方塊，並可讓使用者進行選取。|  
|[CFontDialog::GetCharFormat](#getcharformat)|擷取選取的字型的字元格式。|  
|[CFontDialog::GetColor](#getcolor)|傳回選取的字型色彩。|  
|[CFontDialog::GetCurrentFont](#getcurrentfont)|指派至目前選取的字型特性`LOGFONT`結構。|  
|[CFontDialog::GetFaceName](#getfacename)|傳回選取的字型的字樣名稱。|  
|[CFontDialog::GetSize](#getsize)|傳回選取的字型的點數大小。|  
|[CFontDialog::GetStyleName](#getstylename)|傳回選取的字型樣式名稱。|  
|[CFontDialog::GetWeight](#getweight)|傳回選取的字型粗細。|  
|[CFontDialog::IsBold](#isbold)|決定字型是否為粗體。|  
|[CFontDialog::IsItalic](#isitalic)|決定字型是否為斜體。|  
|[CFontDialog::IsStrikeOut](#isstrikeout)|決定是否要將字型顯示以刪除線。|  
|[CFontDialog::IsUnderline](#isunderline)|決定字型是否加上底線。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CFontDialog::m_cf](#m_cf)|結構，用來自訂`CFontDialog`物件。|  
  
## <a name="remarks"></a>備註  
 A`CFontDialog`物件是目前已安裝在系統中的字型包含清單的對話方塊。 使用者可以從清單中，選取特定字型和此選取項目會接著回報給應用程式。  
  
 若要建構`CFontDialog`物件，使用提供的建構函式或衍生新的子類別，並使用您自己的自訂建構函式。  
  
 一次`CFontDialog`在建構物件，您可以使用`m_cf`結構初始化的值或在對話方塊中控制項的狀態。 [M_cf](#m_cf)結構的類型是[CHOOSEFONT](http://msdn.microsoft.com/library/windows/desktop/ms646832)。 如需有關此結構的詳細資訊，請參閱 Windows SDK。  
  
 在初始化對話方塊物件的控制項之後, 呼叫`DoModal`成員函式來顯示對話方塊，並允許使用者選取的字型。 `DoModal` 傳回使用者是否已選取 確定 (IDOK) 或 取消 (IDCANCEL) 按鈕。  
  
 如果`DoModal`傳回 IDOK，您可以使用其中一個`CFontDialog`的成員函式來擷取使用者所輸入的資訊。  
  
 您可以使用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函式來判斷是否在對話方塊的初始化期間發生錯誤，以及了解錯誤的詳細資訊。 如需有關這個函式的詳細資訊，請參閱 Windows SDK。  
  
 `CFontDialog` 依賴 COMMDLG。隨附於 Windows 版本 3.1 和更新版本的 DLL 檔案。  
  
 若要自訂對話方塊中，衍生的類別`CFontDialog`、 提供自訂對話方塊範本，並新增訊息對應來處理從擴充的控制項通知訊息。 任何未處理的訊息應傳遞至基底類別。  
  
 自訂攔截函式不需要。  
  
 如需有關使用`CFontDialog`，請參閱 <<c2> [ 通用對話方塊類別](../../mfc/common-dialog-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFontDialog`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdlgs.h  
  
##  <a name="cfontdialog"></a>  CFontDialog::CFontDialog  
 建構 `CFontDialog` 物件。  
  
```  
CFontDialog(
    LPLOGFONT lplfInitial = NULL,  
    DWORD dwFlags = CF_EFFECTS | CF_SCREENFONTS,  
    CDC* pdcPrinter = NULL,  
    CWnd* pParentWnd = NULL);

CFontDialog(
    const CHARFORMAT& charformat,  
    DWORD dwFlags = CF_SCREENFONTS,  
    CDC* pdcPrinter = NULL,  
    CWnd* pParentWnd = NULL);  
```  
  
### <a name="parameters"></a>參數  
 *plfInitial*  
 指標[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)資料結構，可讓您設定部分字型的特性。  
  
 *charFormat*  
 指標[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)資料結構，可讓您設定部分字型的特性在 rich edit 控制項。  
  
 *dwFlags*  
 指定一或數個 choose-font 旗標。 可以使用位元 OR 運算子來合併一或數個預先設定的值。 如果您修改 `m_cf.Flag` 結構成員，請務必在您的變更中使用位元 OR 運算子，讓預設行為保持不變。 如需每個這些旗標的詳細資訊，請參閱 popis [CHOOSEFONT](http://msdn.microsoft.com/library/windows/desktop/ms646832) Windows SDK 中的結構。  
  
 *pdcPrinter*  
 printer-device 內容的指標。 若有提供，此參數會指向要選取字型之印表機的 printer-device 內容。  
  
 *pParentWnd*  
 字型對話方塊的父系或擁有者視窗的指標。  
  
### <a name="remarks"></a>備註  
 請注意，建構函式會自動填入 `CHOOSEFONT` 結構的成員中。 您應該只在想要使用不同於預設值的字型對話方塊時，才變更這些設定。  
  
> [!NOTE]
>  唯有在沒有 Rich Edit 控制項支援的情況下，此函式的第一版才會存在。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]  
  
##  <a name="domodal"></a>  CFontDialog::DoModal  
 呼叫此函式可顯示 [Windows 通用字型] 對話方塊中，而且允許使用者選擇字型。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 IDOK 或 IDCANCEL。 如果傳回 IDCANCEL，呼叫 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函式來判斷是否發生錯誤。  
  
 IDOK 及 IDCANCEL 是常數，指出使用者是否已選取 [確定] 或 [取消] 按鈕。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化的各種不同的字型對話方塊控制項[m_cf](#m_cf)結構，您應該執行這項操作之前先呼叫`DoModal`，但在建構對話方塊物件之後。  
  
 如果`DoModal`傳回 IDOK，您可以呼叫其他成員函式來擷取在對話方塊中的 設定 或 使用者的資訊輸入。  
  
### <a name="example"></a>範例  
  請參閱範例[CFontDialog::CFontDialog](#cfontdialog)並[CFontDialog::GetColor](#getcolor)。  
  
##  <a name="getcharformat"></a>  CFontDialog::GetCharFormat  
 擷取選取的字型的字元格式。  
  
```  
void GetCharFormat(CHARFORMAT& cf) const;  
```  
  
### <a name="parameters"></a>參數  
 *cf*  
 A [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)結構，包含選取的字型的字元格式的相關資訊。  
  
##  <a name="getcolor"></a>  CFontDialog::GetColor  
 呼叫此函式來擷取選取的字型色彩。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 選取字型的色彩。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]  
  
##  <a name="getcurrentfont"></a>  CFontDialog::GetCurrentFont  
 呼叫此函式的成員指派的目前選取的字型特性[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構。  
  
```  
void GetCurrentFont(LPLOGFONT lplf);
```  
  
### <a name="parameters"></a>參數  
 *lplf*  
 指標`LOGFONT`結構。  
  
### <a name="remarks"></a>備註  
 其他`CFontDialog`成員函式可供存取個別的目前字型的特性。  
  
 如果在呼叫期間呼叫這個函式[DoModal](#domodal)，它會傳回在目前的選取範圍 (哪些使用者會看到或已在對話方塊中變更)。 如果在呼叫之後呼叫此函式`DoModal`(只有當`DoModal`傳回 IDOK)，它會傳回實際選取的使用者。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]  
  
##  <a name="getfacename"></a>  CFontDialog::GetFaceName  
 呼叫此函式來擷取選取的字型的字樣名稱。  
  
```  
CString GetFaceName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在選取之字型的字樣名稱`CFontDialog` 對話方塊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]  
  
##  <a name="getsize"></a>  CFontDialog::GetSize  
 呼叫此函式來擷取選取的字型的大小。  
  
```  
int GetSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 字型的大小，在某個點的十分之一秒。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]  
  
##  <a name="getstylename"></a>  CFontDialog::GetStyleName  
 呼叫此函式來擷取選取的字型樣式名稱。  
  
```  
CString GetStyleName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 字型的樣式名稱。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]  
  
##  <a name="getweight"></a>  CFontDialog::GetWeight  
 呼叫此函式可擷取所選字型的粗細。  
  
```  
int GetWeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 選取字型的粗細。  
  
### <a name="remarks"></a>備註  
 更多加權字型的詳細資訊，請參閱[CFont::CreateFont](../../mfc/reference/cfont-class.md#createfont)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]  
  
##  <a name="isbold"></a>  CFontDialog::IsBold  
 呼叫此函式來判斷是否選取的字型為粗體。  
  
```  
BOOL IsBold() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果選取的字型已啟用，則粗體的特性，非零值。否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]  
  
##  <a name="isitalic"></a>  CFontDialog::IsItalic  
 呼叫此函式來判斷是否選取的字型為斜體。  
  
```  
BOOL IsItalic() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果選取的字型已啟用，則斜體特性，非零值。否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]  
  
##  <a name="isstrikeout"></a>  CFontDialog::IsStrikeOut  
 呼叫此函式來判斷是否刪除線就會顯示選取的字型。  
  
```  
BOOL IsStrikeOut() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果選取的字型已啟用，則刪除線特性，非零值。否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]  
  
##  <a name="isunderline"></a>  CFontDialog::IsUnderline  
 呼叫此函式可判斷選取的字型會加上底線。  
  
```  
BOOL IsUnderline() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果選取的字型有底線特性啟用，則為非零否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]  
  
##  <a name="m_cf"></a>  CFontDialog::m_cf  
 結構，其成員儲存對話方塊物件的特性。  
  
```  
CHOOSEFONT m_cf;  
```  
  
### <a name="remarks"></a>備註  
 在建構之後`CFontDialog`物件，您可以使用`m_cf`修改各個層面的對話方塊中，然後再呼叫`DoModal`成員函式。 如需有關此結構的詳細資訊，請參閱[CHOOSEFONT](http://msdn.microsoft.com/library/windows/desktop/ms646832) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



