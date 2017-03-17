---
title: "CRichEditView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditView
- AFXRICH/CRichEditView
- AFXRICH/CRichEditView::CRichEditView
- AFXRICH/CRichEditView::AdjustDialogPosition
- AFXRICH/CRichEditView::CanPaste
- AFXRICH/CRichEditView::DoPaste
- AFXRICH/CRichEditView::FindText
- AFXRICH/CRichEditView::FindTextSimple
- AFXRICH/CRichEditView::GetCharFormatSelection
- AFXRICH/CRichEditView::GetDocument
- AFXRICH/CRichEditView::GetInPlaceActiveItem
- AFXRICH/CRichEditView::GetMargins
- AFXRICH/CRichEditView::GetPageRect
- AFXRICH/CRichEditView::GetPaperSize
- AFXRICH/CRichEditView::GetParaFormatSelection
- AFXRICH/CRichEditView::GetPrintRect
- AFXRICH/CRichEditView::GetPrintWidth
- AFXRICH/CRichEditView::GetRichEditCtrl
- AFXRICH/CRichEditView::GetSelectedItem
- AFXRICH/CRichEditView::GetTextLength
- AFXRICH/CRichEditView::GetTextLengthEx
- AFXRICH/CRichEditView::InsertFileAsObject
- AFXRICH/CRichEditView::InsertItem
- AFXRICH/CRichEditView::IsRichEditFormat
- AFXRICH/CRichEditView::OnCharEffect
- AFXRICH/CRichEditView::OnParaAlign
- AFXRICH/CRichEditView::OnUpdateCharEffect
- AFXRICH/CRichEditView::OnUpdateParaAlign
- AFXRICH/CRichEditView::PrintInsideRect
- AFXRICH/CRichEditView::PrintPage
- AFXRICH/CRichEditView::SetCharFormat
- AFXRICH/CRichEditView::SetMargins
- AFXRICH/CRichEditView::SetPaperSize
- AFXRICH/CRichEditView::SetParaFormat
- AFXRICH/CRichEditView::TextNotFound
- AFXRICH/CRichEditView::GetClipboardData
- AFXRICH/CRichEditView::GetContextMenu
- AFXRICH/CRichEditView::IsSelected
- AFXRICH/CRichEditView::OnFindNext
- AFXRICH/CRichEditView::OnInitialUpdate
- AFXRICH/CRichEditView::OnPasteNativeObject
- AFXRICH/CRichEditView::OnPrinterChanged
- AFXRICH/CRichEditView::OnReplaceAll
- AFXRICH/CRichEditView::OnReplaceSel
- AFXRICH/CRichEditView::OnTextNotFound
- AFXRICH/CRichEditView::QueryAcceptData
- AFXRICH/CRichEditView::WrapChanged
- AFXRICH/CRichEditView::m_nBulletIndent
- AFXRICH/CRichEditView::m_nWordWrap
dev_langs:
- C++
helpviewer_keywords:
- document/view architecture, rich edit controls
- OLE containers, rich edit
- rich edit controls, OLE container
- CRichEditView class
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
caps.latest.revision: 25
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
ms.openlocfilehash: 9f54ec0c8aae58828607b01973a263e458c30ddb
ms.lasthandoff: 02/24/2017

---
# <a name="cricheditview-class"></a>CRichEditView 類別
使用[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)和[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)，提供 rich edit 控制項的 MFC 的文件檢視架構內容中的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CRichEditView : public CCtrlView  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CRichEditView::CRichEditView](#cricheditview)|建構 `CRichEditView` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|移動 對話方塊中，使它不會擋目前的選取範圍。|  
|[CRichEditView::CanPaste](#canpaste)|指示剪貼簿是否包含可以貼到 [豐富的編輯] 檢視的資料。|  
|[CRichEditView::DoPaste](#dopaste)|將 OLE 項目貼到此豐富的編輯 檢視。|  
|[CRichEditView::FindText](#findtext)|尋找指定的文字，叫用將等待游標。|  
|[CRichEditView::FindTextSimple](#findtextsimple)|尋找指定的文字。|  
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|擷取格式屬性目前的選取範圍的字元。|  
|[CRichEditView::GetDocument](#getdocument)|擷取相關的指標[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)。|  
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|擷取目前在就地使用豐富的編輯 檢視中的 OLE 項目。|  
|[CRichEditView::GetMargins](#getmargins)|擷取此豐富的編輯 檢視的邊界。|  
|[CRichEditView::GetPageRect](#getpagerect)|擷取此豐富的編輯 檢視的頁框。|  
|[CRichEditView::GetPaperSize](#getpapersize)|擷取此豐富的編輯 檢視的紙張大小。|  
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|擷取段落格式屬性目前的選取範圍。|  
|[CRichEditView::GetPrintRect](#getprintrect)|擷取此豐富的編輯 檢視的列印矩形。|  
|[CRichEditView::GetPrintWidth](#getprintwidth)|擷取此豐富的編輯 檢視的列印寬度。|  
|[Cricheditview:: Getricheditctrl](#getricheditctrl)|擷取的 rich edit 控制項。|  
|[CRichEditView::GetSelectedItem](#getselecteditem)|擷取豐富的編輯 檢視中選取的項目。|  
|[CRichEditView::GetTextLength](#gettextlength)|擷取豐富的編輯 檢視中的文字的長度。|  
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|擷取字元或豐富的編輯 檢視中的位元組的數目。 展開的旗標決定長度的方法清單。|  
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|將檔案插入為 OLE 項目。|  
|[CRichEditView::InsertItem](#insertitem)|插入新項目做為 OLE 項目。|  
|[CRichEditView::IsRichEditFormat](#isricheditformat)|指示剪貼簿是否包含在 rich edit 或文字格式的資料。|  
|[CRichEditView::OnCharEffect](#onchareffect)|切換目前的選取範圍的格式的字元。|  
|[CRichEditView::OnParaAlign](#onparaalign)|變更之段落的對齊方式。|  
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|更新命令 UI 的字元 public 成員函式。|  
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|更新命令 UI 的段落 public 成員函式。|  
|[CRichEditView::PrintInsideRect](#printinsiderect)|將指定的矩形內指定的文字。|  
|[CRichEditView::PrintPage](#printpage)|格式化指定的文字內指定的頁面。|  
|[CRichEditView::SetCharFormat](#setcharformat)|設定格式屬性目前的選取範圍的字元。|  
|[CRichEditView::SetMargins](#setmargins)|設定此豐富的邊界編輯檢視。|  
|[CRichEditView::SetPaperSize](#setpapersize)|設定此豐富的編輯 檢視的紙張大小。|  
|[CRichEditView::SetParaFormat](#setparaformat)|設定段落格式屬性目前的選取範圍。|  
|[CRichEditView::TextNotFound](#textnotfound)|重設控制項的內部搜尋狀態。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CRichEditView::GetClipboardData](#getclipboarddata)|擷取此豐富的編輯 檢視中某個範圍的剪貼簿物件。|  
|[CRichEditView::GetContextMenu](#getcontextmenu)|擷取內容功能表，使用滑鼠右鍵關閉。|  
|[CRichEditView::IsSelected](#isselected)|表示不論，是否選取指定的 OLE 項目。|  
|[CRichEditView::OnFindNext](#onfindnext)|尋找下的一個子字串。|  
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|重新整理檢視時，它是第一個附加至文件。|  
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|OLE 項目擷取原生資料。|  
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|將列印特性設定為指定的裝置。|  
|[CRichEditView::OnReplaceAll](#onreplaceall)|新字串，取代所有出現的指定字串。|  
|[CRichEditView::OnReplaceSel](#onreplacesel)|取代目前的選取範圍。|  
|[CRichEditView::OnTextNotFound](#ontextnotfound)|找不到要求的文字的控制代碼使用者通知。|  
|[CRichEditView::QueryAcceptData](#queryacceptdata)|若要查看有關資料的查詢`IDataObject`。|  
|[CRichEditView::WrapChanged](#wrapchanged)|針對此豐富的編輯的值為基礎的檢視會調整目標輸出裝置`m_nWordWrap`。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|表示項目符號清單的縮排數量。|  
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|表示文字換行條件約束。|  
  
## <a name="remarks"></a>備註  
 「 Rich edit 控制項 」 是一個視窗，讓使用者輸入及編輯文字。 文字字元和段落格式，可以指派，而且可以包含內嵌的 OLE 物件。 Rich edit 控制項來格式化文字，提供程式設計介面。 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。  
  
 `CRichEditView` 會維護文字和文字的格式特性。 `CRichEditDoc`會維護檢視中的 OLE 用戶端項目清單。 `CRichEditCntrItem` 提供 OLE 用戶端項目的存取權給容器端。  
  
 這個 Windows 通用控制項 (並因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相關類別) 僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 下執行的程式和更新版本。  
  
 在 MFC 應用程式中使用豐富的編輯 檢視的範例，請參閱[WORDPAD](../../visual-cpp-samples.md)範例應用程式。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CRichEditView`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrich.h  
  
##  <a name="adjustdialogposition"></a>CRichEditView::AdjustDialogPosition  
 呼叫此函式，讓它不會遮蔽到目前的選取範圍移動指定的對話方塊。  
  
```  
void AdjustDialogPosition(CDialog* pDlg);
```  
  
### <a name="parameters"></a>參數  
 *pDlg*  
 指向 `CDialog` 物件的指標。  
  
##  <a name="canpaste"></a>CRichEditView::CanPaste  
 呼叫此函式可判斷剪貼簿是否包含可以貼到此豐富的編輯 檢視的資訊。  
  
```  
BOOL CanPaste() const;  
```  
  
### <a name="return-value"></a>傳回值  
 剪貼簿資料格式可以接受此豐富的編輯檢視; 如果為非零否則為 0。  
  
##  <a name="cricheditview"></a>CRichEditView::CRichEditView  
 呼叫此函式建立`CRichEditView`物件。  
  
```  
CRichEditView();
```  
  
##  <a name="dopaste"></a>CRichEditView::DoPaste  
 呼叫此函式中的 OLE 項目貼上`dataobj`此豐富的編輯文件/檢視。  
  
```  
void DoPaste(
    COleDataObject& dataobj,  
    CLIPFORMAT cf,  
    HMETAFILEPICT hMetaPict);
```  
  
### <a name="parameters"></a>參數  
 `dataobj`  
 [COleDataObject](../../mfc/reference/coledataobject-class.md)包含要貼上的資料。  
  
 `cf`  
 所需的剪貼簿格式。  
  
 `hMetaPict`  
 中繼檔，表示要貼上項目。  
  
### <a name="remarks"></a>備註  
 架構會呼叫此函式的預設實作的一部分[QueryAcceptData](#queryacceptdata)。  
  
 此函式判斷結果為基礎的處理常式的選擇性貼上貼上的型別。 如果`cf`是 0，則新的項目會使用目前的圖示表示。 如果`cf`為非零值和`hMetaPict`不**NULL**，新的項目會使用`hMetaPict`的表示法。  
  
##  <a name="findtext"></a>CRichEditView::FindText  
 呼叫此函式以尋找指定的文字，並將它設為目前的選取範圍。  
  
```  
BOOL FindText(
    LPCTSTR lpszFind,  
    BOOL bCase = TRUE,  
    BOOL bWord = TRUE,  
    BOOL bNext = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `lpszFind`  
 包含要搜尋的字串。  
  
 `bCase`  
 指出搜尋是否區分大小寫。  
  
 `bWord`  
 表示搜尋應比對全字拼寫須，不是文字的一部份。  
  
 `bNext`  
 表示搜尋方向。 如果**TRUE**，搜尋方向是緩衝區的尾端。 如果**FALSE**，搜尋方向是從緩衝區開頭。  
  
### <a name="return-value"></a>傳回值  
 如果為非零`lpszFind`找到文字; 否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式會尋找作業期間顯示等待游標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&151;](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]  
  
##  <a name="findtextsimple"></a>CRichEditView::FindTextSimple  
 呼叫此函式以尋找指定的文字，並將它設為目前的選取範圍。  
  
```  
BOOL FindTextSimple(
    LPCTSTR lpszFind,  
    BOOL bCase = TRUE,  
    BOOL bWord = TRUE,  
    BOOL bNext = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `lpszFind`  
 包含要搜尋的字串。  
  
 `bCase`  
 指出搜尋是否區分大小寫。  
  
 `bWord`  
 表示搜尋應比對全字拼寫須，不是文字的一部份。  
  
 `bNext`  
 表示搜尋方向。 如果**TRUE**，搜尋方向是緩衝區的尾端。 如果**FALSE**，搜尋方向是從緩衝區開頭。  
  
### <a name="return-value"></a>傳回值  
 如果為非零`lpszFind`找到文字; 否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例[CRichEditView::FindText](#findtext)。  
  
##  <a name="getcharformatselection"></a>CRichEditView::GetCharFormatSelection  
 呼叫此函式可取得的字元格式目前選取範圍的屬性。  
  
```  
CHARFORMAT2& GetCharFormatSelection();
```  
  
### <a name="return-value"></a>傳回值  
 A [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)結構，其中包含的字元格式目前選取範圍的屬性。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_GETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb788026)訊息和[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&152;](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]  
  
##  <a name="getclipboarddata"></a>CRichEditView::GetClipboardData  
 架構會呼叫此函式的處理程序中為[IRichEditOleCallback::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774315)。  
  
```  
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,  
    DWORD dwReco,  
    LPDATAOBJECT lpRichDataObj,  
    LPDATAOBJECT* lplpdataobj);
```  
  
### <a name="parameters"></a>參數  
 `lpchrg`  
 指標[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)結構指定的字元 （和 OLE 項目） 複製到所指定的資料物件範圍`lplpdataobj`。  
  
 `dwReco`  
 剪貼簿作業旗標。 可以是下列值之一。  
  
- **RECO_COPY**複製到剪貼簿。  
  
- **RECO_CUT**剪下到剪貼簿。  
  
- **RECO_DRAG**拖曳作業 （拖曳和卸除）。  
  
- **RECO_DROP**拖放作業 （拖曳和卸除）。  
  
- **RECO_PASTE**從剪貼簿貼。  
  
 `lpRichDataObj`  
 指標[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)物件，其中包含剪貼簿的資料來自 rich edit 控制項 ( [IRichEditOle::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774341))。  
  
 `lplpdataobj`  
 接收的位址指標變數的指標`IDataObject`物件，代表指定之範圍`lpchrg`參數。 值`lplpdataobj`如果傳回的錯誤會被忽略。  
  
### <a name="return-value"></a>傳回值  
 `HRESULT`報告作業成功的值。 如需有關`HRESULT`，請參閱[結構的 COM 錯誤碼](http://msdn.microsoft.com/library/windows/desktop/ms690088)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 如果傳回值表示成功， **IRichEditOleCallback::GetClipboardData**傳回`IDataObject`存取`lplpdataobj`，否則會傳回一個由`lpRichDataObj`。 覆寫此函式可提供您自己的剪貼簿資料。 此函式的預設實作會傳回**E_NOTIMPL**。  
  
 這是進階可覆寫。  
  
 如需詳細資訊，請參閱[IRichEditOle::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774341)， [IRichEditOleCallback::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774315)，和[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]看[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)中[!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
##  <a name="getcontextmenu"></a>CRichEditView::GetContextMenu  
 架構會呼叫此函式的處理程序中為[IRichEditOleCallback::GetContextMenu](http://msdn.microsoft.com/library/windows/desktop/bb774317)。  
  
```  
virtual HMENU GetContextMenu(
    WORD seltyp,  
    LPOLEOBJECT lpoleobj,  
    CHARRANGE* lpchrg);
```  
  
### <a name="parameters"></a>參數  
 *seltyp*  
 選取項目型別。 選取項目類型的值是 < 備註 > 一節所述。  
  
 `lpoleobj`  
 指標**OLEOBJECT**結構，指定第一個選取的 OLE 物件，如果選取範圍包含一或多個 OLE 項目。 如果選取範圍不包含任何項目，`lpoleobj`是**NULL**。 **OLEOBJECT**結構包含 OLE 物件的 v-資料表的指標。  
  
 `lpchrg`  
 指標[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)結構，其中包含目前的選取範圍。  
  
### <a name="return-value"></a>傳回值  
 內容功能表的控制代碼。  
  
### <a name="remarks"></a>備註  
 此函式是常見的一部分處理下的右滑鼠按鈕。  
  
 選取項目類型可以是下列旗標的任意組合︰  
  
- `SEL_EMPTY`表示目前的選取範圍。  
  
- `SEL_TEXT`指出目前的選取範圍包含文字。  
  
- `SEL_OBJECT`指出目前的選取範圍包含至少一個 OLE 項目。  
  
- `SEL_MULTICHAR`指出目前的選取範圍包含多個文字字元。  
  
- `SEL_MULTIOBJECT`指出目前的選取範圍包含一個以上的 OLE 物件。  
  
 預設實作會傳回**NULL**。 這是進階可覆寫。  
  
 如需詳細資訊，請參閱[IRichEditOleCallback::GetContextMenu](http://msdn.microsoft.com/library/windows/desktop/bb774317)和[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需有關**OLEOBJECT**類型，請參閱 OLE 資料結構和結構配置文件，在*OLE 知識庫*。  
  
##  <a name="getdocument"></a>CRichEditView::GetDocument  
 呼叫此函式可取得的指標`CRichEditDoc`與此檢視相關聯。  
  
```  
CRichEditDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)物件相關聯程式`CRichEditView`物件。  
  
##  <a name="getinplaceactiveitem"></a>CRichEditView::GetInPlaceActiveItem  
 呼叫此函式可取得 OLE 項目中這目前已啟動`CRichEditView`物件。  
  
```  
CRichEditCntrItem* GetInPlaceActiveItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 單一的就地使用中的指標[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)物件在此豐富的編輯 檢視中。**NULL**如果沒有 OLE 項目目前就地作用中狀態。  
  
##  <a name="getmargins"></a>CRichEditView::GetMargins  
 呼叫此函式可擷取目前用於列印的邊界。  
  
```  
CRect GetMargins() const;  
```  
  
### <a name="return-value"></a>傳回值  
 用於列印，邊界以`MM_TWIPS`。  
  
##  <a name="getpagerect"></a>CRichEditView::GetPageRect  
 呼叫此函式可取得用於列印頁面的尺寸。  
  
```  
CRect GetPageRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 用於列印的頁面範圍以`MM_TWIPS`。  
  
### <a name="remarks"></a>備註  
 這個值會根據紙張大小。  
  
##  <a name="getpapersize"></a>CRichEditView::GetPaperSize  
 呼叫此函式可擷取目前的紙張大小。  
  
```  
CSize GetPaperSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 用於列印的紙張大小以單位`MM_TWIPS`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&153;](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]  
  
##  <a name="getparaformatselection"></a>CRichEditView::GetParaFormatSelection  
 呼叫此函式可取得的段落格式化目前選取範圍的屬性。  
  
```  
PARAFORMAT2& GetParaFormatSelection();
```  
  
### <a name="return-value"></a>傳回值  
 A [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)所在的段落格式屬性，在目前選取的結構。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[EM_GETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774182)訊息和[PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getprintrect"></a>CRichEditView::GetPrintRect  
 呼叫此函式可擷取頁面矩形內的列印區域的範圍。  
  
```  
CRect GetPrintRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 用於列印，在影像區域的界限是以`MM_TWIPS`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&154;](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]  
  
##  <a name="getprintwidth"></a>CRichEditView::GetPrintWidth  
 呼叫此函式可判斷列印區域的寬度。  
  
```  
int GetPrintWidth() const;  
```  
  
### <a name="return-value"></a>傳回值  
 列印區域的寬度以`MM_TWIPS`。  
  
##  <a name="getricheditctrl"></a>Cricheditview:: Getricheditctrl  
 呼叫此函式可擷取[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)物件相關聯`CRichEditView`物件。  
  
```  
CRichEditCtrl& GetRichEditCtrl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `CRichEditCtrl`此檢視的物件。  
  
### <a name="example"></a>範例  
  請參閱範例[CRichEditView::FindText](#findtext)。  
  
##  <a name="getselecteditem"></a>CRichEditView::GetSelectedItem  
 呼叫此函式可擷取 OLE 項目 (`CRichEditCntrItem`物件) 目前在此選取`CRichEditView`物件。  
  
```  
CRichEditCntrItem* GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)中所選取物件`CRichEditView`物件;**NULL**如果在這個檢視中不選取任何項目。  
  
##  <a name="gettextlength"></a>CRichEditView::GetTextLength  
 呼叫此函式，以取得在這個文字的長度`CRichEditView`物件。  
  
```  
long GetTextLength() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在這個文字的長度`CRichEditView`物件。  
  
##  <a name="gettextlengthex"></a>CRichEditView::GetTextLengthEx  
 呼叫此成員函式，來計算中的文字長度`CRichEditView`物件。  
  
```  
long GetTextLengthEx(
    DWORD dwFlags,  
    UINT uCodePage = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 值，指定要用來判斷文字長度的方法。 這個成員可以是其中一個或多個值中的旗標成員列出[GETTEXTLENGTHEX](http://msdn.microsoft.com/library/windows/desktop/bb787915)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `uCodePage`  
 翻譯 (CP_ACP ANSI 字碼頁，unicode 1200) 的字碼頁。  
  
### <a name="return-value"></a>傳回值  
 字元或編輯控制項中的位元組數目。 如果在已設定不相容的旗標`dwFlags`，此成員函式會傳回`E_INVALIDARG`。  
  
### <a name="remarks"></a>備註  
 `GetTextLengthEx`提供其他方法，判斷文字的長度。 它支援豐富的編輯 2.0 的功能。 如需詳細資訊，請參閱[有關 Rich Edit 控制項](http://msdn.microsoft.com/library/windows/desktop/bb787873)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="insertfileasobject"></a>CRichEditView::InsertFileAsObject  
 呼叫此函式，將指定的檔案 (做為[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)物件) 讀入 rich 編輯檢視。  
  
```  
void InsertFileAsObject(LPCTSTR lpszFileName);
```  
  
### <a name="parameters"></a>參數  
 `lpszFileName`  
 字串，包含要插入的檔案名稱。  
  
##  <a name="insertitem"></a>CRichEditView::InsertItem  
 呼叫此函式插入[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)豐富的編輯檢視的物件。  
  
```  
HRESULT InsertItem(CRichEditCntrItem* pItem);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 要插入之項目的指標。  
  
### <a name="return-value"></a>傳回值  
 `HRESULT`值，指出成功的插入。  
  
### <a name="remarks"></a>備註  
 如需有關`HRESULT`，請參閱[結構的 COM 錯誤碼](http://msdn.microsoft.com/library/windows/desktop/ms690088)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="isricheditformat"></a>CRichEditView::IsRichEditFormat  
 呼叫此函式來判斷如果`cf`是剪貼簿格式，也就是文字、 豐富的文字或 rtf 文字與 OLE 項目。  
  
```  
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```  
  
### <a name="parameters"></a>參數  
 `cf`  
 感興趣的剪貼簿格式。  
  
### <a name="return-value"></a>傳回值  
 如果為非零`cf`是豐富的編輯] 或 [文字剪貼簿格式。  
  
##  <a name="isselected"></a>CRichEditView::IsSelected  
 呼叫此函式來判斷指定的 OLE 項目目前在此檢視中選取。  
  
```  
virtual BOOL IsSelected(const CObject* pDocItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `pDocItem`  
 在檢視中物件的指標。  
  
### <a name="return-value"></a>傳回值  
 非零，如果有選取的物件。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您的衍生的檢視類別具有不同的方法來處理 OLE 項目的選取範圍，請覆寫這個函式。  
  
##  <a name="m_nbulletindent"></a>CRichEditView::m_nBulletIndent  
 縮排項目符號中的項目清單。根據預設，720 單位，也就是 1/2 英吋。  
  
```  
int m_nBulletIndent;  
```  
  
##  <a name="m_nwordwrap"></a>CRichEditView::m_nWordWrap  
 表示此豐富的編輯 檢視的自動換行的類型。  
  
```  
int m_nWordWrap;  
```  
  
### <a name="remarks"></a>備註  
 下列其中一個值：  
  
- `WrapNone`表示沒有自動的自動換行。  
  
- `WrapToWindow`表示根據視窗寬度的文字換行。  
  
- `WrapToTargetDevice`表示目標裝置的特性為基礎的自動換行。  
  
### <a name="example"></a>範例  
  請參閱範例[CRichEditView::WrapChanged](#wrapchanged)。  
  
##  <a name="onchareffect"></a>CRichEditView::OnCharEffect  
 呼叫此函式可切換的格式化效果目前選取範圍的字元。  
  
```  
void OnCharEffect(
    DWORD dwMask,  
    DWORD dwEffect);
```  
  
### <a name="parameters"></a>參數  
 `dwMask`  
 格式化效果來修改目前的選取範圍中的字元。  
  
 `dwEffect`  
 字元格式可切換的效果所需的清單。  
  
### <a name="remarks"></a>備註  
 每次呼叫此函式來切換目前選取範圍指定的格式化效果。  
  
 如需有關`dwMask`和`dwEffect`參數和可能的值，請參閱對應的資料成員的[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&155;](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]  
  
##  <a name="onfindnext"></a>CRichEditView::OnFindNext  
 處理命令的 [尋找/取代] 對話方塊時，由架構呼叫。  
  
```  
virtual void OnFindNext(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    BOOL bWord);
```  
  
### <a name="parameters"></a>參數  
 `lpszFind`  
 要尋找的字串。  
  
 `bNext`  
 要搜尋的方向︰ **TRUE**表示關閉。**FALSE**, up.  
  
 `bCase`  
 指出搜尋是否不區分大小寫。  
  
 `bWord`  
 指出搜尋是否只或不符合整個單字。  
  
### <a name="remarks"></a>備註  
 呼叫此函式內搜尋文字`CRichEditView`。 覆寫這個函式來變更搜尋特性衍生的檢視類別。  
  
##  <a name="oninitialupdate"></a>CRichEditView::OnInitialUpdate  
 檢視第一次連接到文件之後，但一開始會顯示檢視之前，由架構呼叫。  
  
```  
virtual void OnInitialUpdate();
```  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會呼叫[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)成員函式，而沒有提示的資訊 (也就使用預設值為 0，表示`lHint`參數和**NULL**的`pHint`參數)。 覆寫這個函式來執行任何需要文件的相關資訊的單次初始化。 比方說，如果您的應用程式有固定大小的文件，您可以使用此函式來初始化檢視的捲動根據文件大小的限制。 如果您的應用程式支援可變大小的文件，使用`OnUpdate`來更新使用者在每次文件會將變更限制。  
  
### <a name="example"></a>範例  
  請參閱範例[CRichEditView::m_nWordWrap](#m_nwordwrap)。  
  
##  <a name="onpastenativeobject"></a>CRichEditView::OnPasteNativeObject  
 您可以使用此函式，內嵌項目載入原生資料。  
  
```  
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```  
  
### <a name="parameters"></a>參數  
 *lpStg*  
 指標[IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015)物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 一般而言，您可以這樣藉由建立[COleStreamFile](../../mfc/reference/colestreamfile-class.md)周圍`IStorage`。 `COleStreamFile`可以附加至封存檔和[CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)呼叫以將資料載入。  
  
 這是進階可覆寫。  
  
 如需詳細資訊，請參閱[IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onparaalign"></a>CRichEditView::OnParaAlign  
 呼叫此函式來變更所選段落中的段落對齊方式。  
  
```  
void OnParaAlign(WORD wAlign);
```  
  
### <a name="parameters"></a>參數  
 `wAlign`  
 所需的段落對齊方式。 下列其中一個值：  
  
- `PFA_LEFT`對齊左邊界的段落。  
  
- `PFA_RIGHT`對齊右邊界的段落。  
  
- `PFA_CENTER`置中對齊邊界的段落。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&156;](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]  
  
##  <a name="onprinterchanged"></a>CRichEditView::OnPrinterChanged  
 覆寫這個函式來變更印表機時，變更此豐富的編輯 檢視的特性。  
  
```  
virtual void OnPrinterChanged(const CDC& dcPrinter);
```  
  
### <a name="parameters"></a>參數  
 `dcPrinter`  
 A [CDC](../../mfc/reference/cdc-class.md)新印表機的物件。  
  
### <a name="remarks"></a>備註  
 預設實作會將紙張大小設定為實體的高度和寬度的輸出裝置 （印表機）。 如果沒有任何裝置內容會與相關聯`dcPrinter`，預設實作會將紙張大小設定為 8.5 11 英吋。  
  
##  <a name="onreplaceall"></a>CRichEditView::OnReplaceAll  
 處理來自 [取代] 對話方塊中的全部取代命令時，由架構呼叫。  
  
```  
virtual void OnReplaceAll(
    LPCTSTR lpszFind,  
    LPCTSTR lpszReplace,  
    BOOL bCase,  
    BOOL bWord);
```  
  
### <a name="parameters"></a>參數  
 `lpszFind`  
 要被取代的文字。  
  
 `lpszReplace`  
 取代的文字。  
  
 `bCase`  
 指出搜尋是否區分大小寫。  
  
 `bWord`  
 表示搜尋是否必須選取整個單字。  
  
### <a name="remarks"></a>備註  
 呼叫此函式以另一個字串來取代所有出現的一些特定的文字。 覆寫這個函式來變更此檢視的搜尋特性。  
  
### <a name="example"></a>範例  
  請參閱範例[CRichEditView::FindText](#findtext)。  
  
##  <a name="onreplacesel"></a>CRichEditView::OnReplaceSel  
 處理 [取代] 對話方塊中的取代命令時，由架構呼叫。  
  
```  
virtual void OnReplaceSel(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    BOOL bWord,  
    LPCTSTR lpszReplace);
```  
  
### <a name="parameters"></a>參數  
 `lpszFind`  
 要被取代的文字。  
  
 `bNext`  
 表示搜尋方向︰ **TRUE**已關閉。**FALSE**, up.  
  
 `bCase`  
 指出搜尋是否區分大小寫。  
  
 `bWord`  
 表示搜尋是否必須選取整個單字。  
  
 `lpszReplace`  
 取代的文字。  
  
### <a name="remarks"></a>備註  
 呼叫此函式出現一次某些指定的文字取代為另一個字串。 覆寫這個函式來變更此檢視的搜尋特性。  
  
##  <a name="ontextnotfound"></a>CRichEditView::OnTextNotFound  
 每當搜尋失敗時，由架構呼叫。  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>參數  
 `lpszFind`  
 找不到文字。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來變更輸出通知從[MessageBeep](http://msdn.microsoft.com/library/windows/desktop/ms680356)。  
  
 如需詳細資訊，請參閱[MessageBeep](http://msdn.microsoft.com/library/windows/desktop/ms680356)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&157;](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]  
  
##  <a name="onupdatechareffect"></a>CRichEditView::OnUpdateCharEffect  
 架構會呼叫此函式可更新命令 UI 字元效果命令。  
  
```  
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,  
    DWORD dwMask,  
    DWORD dwEffect);
```  
  
### <a name="parameters"></a>參數  
 `pCmdUI`  
 指標[CCmdUI](../../mfc/reference/ccmdui-class.md)物件。  
  
 `dwMask`  
 表示格式化遮罩的字元。  
  
 `dwEffect`  
 表示的字元格式的效果。  
  
### <a name="remarks"></a>備註  
 遮罩`dwMask`指定的字元格式化屬性來檢查。 旗標`dwEffect`清單的字元格式設定/清除的屬性。  
  
 如需有關`dwMask`和`dwEffect`參數和可能的值，請參閱對應的資料成員的[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&158;](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]  
  
##  <a name="onupdateparaalign"></a>CRichEditView::OnUpdateParaAlign  
 架構會呼叫此函式可更新命令 UI 段落效果命令。  
  
```  
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,  
    WORD wAlign);
```  
  
### <a name="parameters"></a>參數  
 `pCmdUI`  
 指標[CCmdUI](../../mfc/reference/ccmdui-class.md)物件。  
  
 `wAlign`  
 若要檢查段落對齊方式。 下列其中一個值：  
  
- `PFA_LEFT`對齊左邊界的段落。  
  
- `PFA_RIGHT`對齊右邊界的段落。  
  
- `PFA_CENTER`置中對齊邊界的段落。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&159;](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]  
  
##  <a name="printinsiderect"></a>CRichEditView::PrintInsideRect  
 呼叫此函式可設定以符合 rich edit 控制項中的文字範圍的格式*rectLayout*所指定的裝置`pDC`。  
  
```  
long PrintInsideRect(
    CDC* pDC,  
    RECT& rectLayout,  
    long nIndexStart,  
    long nIndexStop,  
    BOOL bOutput);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 在輸出區域的裝置內容的指標。  
  
 *rectLayout*  
 [RECT](../../mfc/reference/rect-structure1.md)或[CRect](../../atl-mfc-shared/reference/crect-class.md)定義輸出區域。  
  
 `nIndexStart`  
 要格式化的第一個字元之以零起始的索引。  
  
 `nIndexStop`  
 要格式化的最後一個字元的以零為起始的索引。  
  
 *bOutput*  
 指出是否應該轉譯文字。 如果**FALSE**，只測量的文字。  
  
### <a name="return-value"></a>傳回值  
 適合於輸出區域加一的最後一個字元索引。  
  
### <a name="remarks"></a>備註  
 一般而言，此呼叫後面呼叫[CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband)產生輸出。  
  
### <a name="example"></a>範例  
  請參閱範例[CRichEditView::GetPaperSize](#getpapersize)。  
  
##  <a name="printpage"></a>CRichEditView::PrintPage  
 呼叫此函式可設定所指定的輸出裝置的 rich edit 控制項中的文字範圍的格式`pDC`。  
  
```  
long PrintPage(
    CDC* pDC,  
    long nIndexStart,  
    long nIndexStop);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 網頁輸出的裝置內容的指標。  
  
 `nIndexStart`  
 要格式化的第一個字元之以零起始的索引。  
  
 `nIndexStop`  
 要格式化的最後一個字元的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 在頁面加一的最後一個字元索引。  
  
### <a name="remarks"></a>備註  
 每個頁面的版面配置由控制[GetPageRect](#getpagerect)和[GetPrintRect](#getprintrect)。 一般而言，此呼叫後面呼叫[CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband)產生輸出。  
  
 請注意，是相對於實體頁面上，而不是邏輯頁面的邊界。 因此，由於許多印表機無法列印頁面上的區域邊界的零會經常裁剪文字。 若要避免裁剪文字，您應該呼叫[SetMargins](#setmargins)和設定列印之前先合理的邊界。  
  
##  <a name="queryacceptdata"></a>CRichEditView::QueryAcceptData  
 若要將物件貼到豐富的編輯架構呼叫。  
  
```  
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,  
    CLIPFORMAT* lpcfFormat,  
    DWORD dwReco,  
    BOOL bReally,  
    HGLOBAL hMetaFile);
```  
  
### <a name="parameters"></a>參數  
 *lpdataobj*  
 指標[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)查詢。  
  
 *lpcfFormat*  
 可接受的資料格式的指標。  
  
 `dwReco`  
 未使用。  
  
 *bReally*  
 表示是否貼上作業應該繼續進行。  
  
 `hMetaFile`  
 用來繪製項目的圖示中繼檔案控制代碼。  
  
### <a name="return-value"></a>傳回值  
 `HRESULT`報告作業成功的值。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來處理不同的組織，COM 中的項目衍生的文件類別。 這是進階可覆寫。  
  
 如需有關`HRESULT`和`IDataObject`，請參閱[COM 錯誤代碼結構](http://msdn.microsoft.com/library/windows/desktop/ms690088)和[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)，分別在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&160;](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]  
  
##  <a name="setcharformat"></a>CRichEditView::SetCharFormat  
 呼叫此函式可設定的字元格式中的新文字屬性`CRichEditView`物件。  
  
```  
void SetCharFormat(CHARFORMAT2 cf);
```  
  
### <a name="parameters"></a>參數  
 `cf`  
 [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)結構，其中包含新的預設字元格式的屬性。  
  
### <a name="remarks"></a>備註  
 只有屬性所指定**dwMask**成員`cf`中變更此函式。  
  
 如需詳細資訊，請參閱[EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230)訊息和[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&152;](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]  
  
##  <a name="setmargins"></a>CRichEditView::SetMargins  
 呼叫此函式可設定此豐富的編輯 檢視的列印邊界。  
  
```  
void SetMargins(const CRect& rectMargin);
```  
  
### <a name="parameters"></a>參數  
 *rectMargin*  
 新的邊界值，用於列印，以測量`MM_TWIPS`。  
  
### <a name="remarks"></a>備註  
 如果[m_nWordWrap](#m_nwordwrap)是`WrapToTargetDevice`，您應該呼叫[WrapChanged](#wrapchanged)之後使用這個函式來調整列印特性。  
  
 請注意，所使用的邊界[PrintPage](#printpage)相對於實體頁面上，而不是邏輯頁面。 因此，由於許多印表機無法列印頁面上的區域邊界的零會經常裁剪文字。 若要避免裁剪文字，您應該呼叫使用`SetMargins`設定適當的印表機列印之前的邊界。  
  
### <a name="example"></a>範例  
  請參閱範例[CRichEditView::GetPaperSize](#getpapersize)。  
  
##  <a name="setpapersize"></a>CRichEditView::SetPaperSize  
 呼叫此函式以設定紙張大小來列印此豐富的編輯 檢視。  
  
```  
void SetPaperSize(CSize sizePaper);
```  
  
### <a name="parameters"></a>參數  
 *sizePaper*  
 新的紙張大小值，用於列印，以測量`MM_TWIPS`。  
  
### <a name="remarks"></a>備註  
 如果[m_nWordWrap](#m_nwordwrap)是`WrapToTargetDevice`，您應該呼叫[WrapChanged](#wrapchanged)之後使用這個函式來調整列印特性。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&161;](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]  
  
##  <a name="setparaformat"></a>CRichEditView::SetParaFormat  
 呼叫此函式可設定段落格式屬性目前的選取範圍，在此`CRichEditView`物件。  
  
```  
BOOL SetParaFormat(PARAFORMAT2& pf);
```  
  
### <a name="parameters"></a>參數  
 `pf`  
 [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)結構，其中包含新的預設段落格式屬性。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 只有屬性所指定**dwMask**成員`pf`中變更此函式。  
  
 如需詳細資訊，請參閱[EM_SETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774276)訊息和[PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&162;](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]  
  
##  <a name="textnotfound"></a>CRichEditView::TextNotFound  
 呼叫此函式來重設的內部搜尋狀態[CRichEditView](../../mfc/reference/cricheditview-class.md)失敗呼叫後的控制項[FindText](#findtext)。  
  
```  
void TextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>參數  
 `lpszFind`  
 包含找不到文字字串。  
  
### <a name="remarks"></a>備註  
 我們建議您呼叫這個方法，失敗的呼叫之後立即[FindText](#findtext)使控制項的內部搜尋狀態正確重設。  
  
 `lpszFind`參數應包含相同的內容當做字串提供給[FindText](#findtext)。 重設內部搜尋狀態之後, 會呼叫這個方法[OnTextNotFound](#ontextnotfound)方法，使用提供的搜尋字串。  
  
### <a name="example"></a>範例  
  請參閱範例[CRichEditView::FindText](#findtext)。  
  
##  <a name="wrapchanged"></a>CRichEditView::WrapChanged  
 變更列印特性時，呼叫此函式 ( [SetMargins](#setmargins)或[SetPaperSize](#setpapersize))。  
  
```  
virtual void WrapChanged();
```  
  
### <a name="remarks"></a>備註  
 此函式來修改 rich edit 檢視的方式回應中的變更覆寫[m_nWordWrap](#m_nwordwrap)或列印的特性 ( [OnPrinterChanged](#onprinterchanged))。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&163;](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 WORDPAD](../../visual-cpp-samples.md)   
 [CCtrlView 類別](../../mfc/reference/cctrlview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc 類別](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditCntrItem 類別](../../mfc/reference/cricheditcntritem-class.md)

