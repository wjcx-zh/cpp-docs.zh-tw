---
title: CButton 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
dev_langs:
- C++
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9932f8814855213f133323f2102e0cacf1e69c8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196707"
---
# <a name="cbutton-class"></a>CButton 類別
提供 Windows 按鈕控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CButton : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CButton::CButton](#cbutton)|建構 `CButton` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CButton::Create](#create)|建立 Windows 按鈕控制項，並將它附加至`CButton`物件。|  
|[CButton::DrawItem](#drawitem)|若要繪製主控描繪的覆寫`CButton`物件。|  
|[CButton::GetBitmap](#getbitmap)|擷取先前設定之點陣圖的控制代碼[SetBitmap](#setbitmap)。|  
|[CButton::GetButtonStyle](#getbuttonstyle)|擷取相關的按鈕控制項的樣式資訊。|  
|[CButton::GetCheck](#getcheck)|擷取的按鈕控制項的核取狀態。|  
|[CButton::GetCursor](#getcursor)|使用先前設定的游標影像控制代碼的擷取[SetCursor](#setcursor)。|  
|[CButton::GetIcon](#geticon)|擷取先前設定之圖示的控制代碼[SetIcon](#seticon)。|  
|[CButton::GetIdealSize](#getidealsize)|擷取的理想大小的按鈕控制項。|  
|[CButton::GetImageList](#getimagelist)|擷取映像清單的按鈕控制項。|  
|[CButton::GetNote](#getnote)|擷取目前的命令連結控制項的附註元件。|  
|[CButton::GetNoteLength](#getnotelength)|擷取目前的命令連結控制項的註解文字的長度。|  
|[CButton::GetSplitGlyph](#getsplitglyph)|擷取目前的分割按鈕控制項相關聯的圖像。|  
|[CButton::GetSplitImageList](#getsplitimagelist)|擷取目前的分割按鈕控制項的影像清單。|  
|[CButton::GetSplitInfo](#getsplitinfo)|擷取定義目前的分割按鈕控制項的資訊。|  
|[CButton::GetSplitSize](#getsplitsize)|擷取目前的分割按鈕控制項的下拉式清單元件的週框矩形。|  
|[CButton::GetSplitStyle](#getsplitstyle)|擷取定義目前的分割按鈕控制項的分割按鈕樣式。|  
|[CButton::GetState](#getstate)|擷取核取狀態、 反白顯示的狀態，以及按鈕控制項的焦點狀態。|  
|[CButton::GetTextMargin](#gettextmargin)|擷取按鈕控制項的文字邊界。|  
|[CButton::SetBitmap](#setbitmap)|指定要在按鈕上顯示的點陣圖。|  
|[CButton::SetButtonStyle](#setbuttonstyle)|變更按鈕的樣式。|  
|[CButton::SetCheck](#setcheck)|設定按鈕控制項的核取狀態。|  
|[CButton::SetCursor](#setcursor)|指定要在按鈕上顯示的游標映像。|  
|[CButton::SetDropDownState](#setdropdownstate)|設定目前的分割按鈕控制項的下拉式清單狀態。|  
|[CButton::SetIcon](#seticon)|指定要在按鈕上顯示的圖示。|  
|[CButton::SetImageList](#setimagelist)|設定按鈕控制項影像清單。|  
|[CButton::SetNote](#setnote)|設定目前的命令連結控制項的附註。|  
|[CButton::SetSplitGlyph](#setsplitglyph)|將指定的圖像 （glyph） 與目前的分割按鈕控制項產生關聯。|  
|[CButton::SetSplitImageList](#setsplitimagelist)|將影像清單與目前的分割按鈕控制項產生關聯。|  
|[CButton::SetSplitInfo](#setsplitinfo)|指定定義目前的分割按鈕控制項的資訊。|  
|[CButton::SetSplitSize](#setsplitsize)|設定目前的分割按鈕控制項的下拉式清單元件的週框矩形。|  
|[CButton::SetSplitStyle](#setsplitstyle)|設定目前的分割按鈕控制項的樣式。|  
|[CButton::SetState](#setstate)|設定反白顯示的按鈕控制項的狀態。|  
|[CButton::SetTextMargin](#settextmargin)|設定按鈕控制項的文字邊界。|  
  
## <a name="remarks"></a>備註  
 按鈕控制項是可以在開啟或關閉按一下小型的矩形的子視窗。 按鈕可以單獨使用或在群組和可以被標示為或不包含文字會出現。 當使用者按一下按鈕通常會變更外觀。  
  
 一般的按鈕是核取方塊、 選項按鈕和按鈕。 A`CButton`物件可以成為任何這些項目，根據[按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)指定在其初始化所[建立](#create)成員函式。  
  
 颾魤 ㄛ [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)類別衍生自`CButton`支援加上而不是文字的點陣圖影像的按鈕控制項的建立。 A`CBitmapButton`可以有不同的點陣圖按鈕的、 向下已取得焦點，和停用狀態。  
  
 從對話方塊範本，或是直接在您的程式碼中，您可以建立的按鈕控制項。 在這兩種情況下，第一次呼叫建構函式`CButton`來建構`CButton`物件，然後呼叫`Create`成員函式來建立 Windows 按鈕控制項，並將其附加至`CButton`物件。  
  
 建構可以是單一步驟中的處理序類別，衍生自`CButton`。 寫入的建構函式在衍生的類別並呼叫`Create`從建構函式內。  
  
 如果您想要處理 Windows 通知訊息傳送給其父代的按鈕控制項 (通常是從衍生的類別[CDialog](../../mfc/reference/cdialog-class.md))，將訊息對應項目和訊息處理常式成員函式新增至每個訊息的父類別。  
  
 每個訊息對應項目都會使用下列格式：  
  
 **ON_** 通知 **(**`id`， `memberFxn` **)**  
  
 何處`id`指定傳送通知之控制項的子視窗識別碼和`memberFxn`是您撰寫來處理通知的父成員函式的名稱。  
  
 父代的函式原型如下所示：  
  
 **afx_msg** `void` `memberFxn` **（);**  
  
 可能的訊息對應項目如下所示：  
  
|對應項目|傳送到父系時...|  
|---------------|----------------------------|  
|ON_BN_CLICKED|使用者按一下按鈕。|  
|ON_BN_DOUBLECLICKED|使用者按兩下按鈕。|  
  
 如果您建立`CButton`物件從對話方塊資源，`CButton`使用者關閉對話方塊時，即會自動終結物件。  
  
 如果您建立`CButton`物件內的視窗中，您可能需要終結它。 如果您建立`CButton`物件上使用堆積**新**函式，您必須呼叫**刪除**物件終結它，當使用者關閉 Windows 按鈕控制項。 如果您建立`CButton`堆疊，或它的物件內嵌於父對話方塊物件，它會自動終結。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CButton`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cbutton"></a>  CButton::CButton  
 建構 `CButton` 物件。  
  
```  
CButton();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]  
  
##  <a name="create"></a>  CButton::Create  
 建立 Windows 按鈕控制項，並將它附加至`CButton`物件。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *lpszCaption*  
 指定按鈕控制項的文字。  
  
 *cheaderctrl:: Create*  
 指定按鈕控制項的樣式。 套用的任何組合[按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)按鈕。  
  
 *rect*  
 指定按鈕控制項的大小和位置。 它可以是`CRect`物件或`RECT`結構。  
  
 *pParentWnd*  
 指定按鈕控制項的父視窗，通常`CDialog`。 它必須不是 NULL。  
  
 *nID*  
 指定按鈕控制項的識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CButton`兩個步驟中的物件。 首先，呼叫建構函式，然後呼叫`Create`，這會建立 Windows 按鈕控制項，並將它附加至`CButton`物件。  
  
 如果 WS_VISIBLE 樣式已有指定，Windows 將會啟動並顯示按鈕所需的所有訊息時都傳送的按鈕控制項。  
  
 套用下列[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)按鈕控制項：  
  
- WS_CHILD 一律  
  
- WS_VISIBLE 通常  
  
- WS_DISABLED 很少  
  
- WS_GROUP 群組控制項  
  
- WS_TABSTOP 若要用 tab 鍵順序來包含按鈕  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]  
  
##  <a name="drawitem"></a>  CButton::DrawItem  
 當主控描繪按鈕的視覺外觀變更時由架構呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 *lpDrawItemStruct*  
 長指標[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)結構。 此結構包含要繪製的項目和繪圖所需的類型資訊。  
  
### <a name="remarks"></a>備註  
 為主控描繪按鈕具有 BS_OWNERDRAW 樣式集。 覆寫此成員函式，來實作活動，抽獎獲得描繪`CButton`物件。 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件*lpDrawItemStruct*之前的成員函式會結束。  
  
 另請參閱[BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles)樣式值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]  
  
##  <a name="getbitmap"></a>  CButton::GetBitmap  
 呼叫此成員函式，以取得點陣圖，使用先前設定的控制代碼[SetBitmap](#setbitmap)，也就是與按鈕相關聯。  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>傳回值  
 點陣圖控制代碼。 如果沒有點陣圖先前指定，則為 NULL。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="getbuttonstyle"></a>  CButton::GetButtonStyle  
 擷取相關的按鈕控制項的樣式資訊。  
  
```  
UINT GetButtonStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回這個按鈕樣式`CButton`物件。 此函式只會傳回[BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles)樣式值，不是任何其他的視窗樣式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="getcheck"></a>  CButton::GetCheck  
 擷取選項按鈕或核取方塊的核取的狀態。  
  
```  
int GetCheck() const;  
```  
  
### <a name="return-value"></a>傳回值  
 使用 BS_AUTOCHECKBOX、 BS_AUTORADIOBUTTON、 BS_AUTO3STATE、 BS_CHECKBOX、 BS_RADIOBUTTON，建立的按鈕控制項的傳回值或 BS_3STATE 樣式是下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|BST_UNCHECKED|未選取按鈕狀態。|  
|BST_CHECKED|按鈕狀態會檢查。|  
|BST_INDETERMINATE|按鈕狀態 （僅適用於按鈕具有 BS_3STATE 或 BS_AUTO3STATE 樣式時）。|  
  
 如果按鈕有任何其他樣式，則傳回的值會是 BST_UNCHECKED。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="getcursor"></a>  CButton::GetCursor  
 呼叫此成員函式取得的資料指標，使用先前設定的控制代碼[SetCursor](#setcursor)，也就是與按鈕相關聯。  
  
```  
HCURSOR GetCursor();  
```  
  
### <a name="return-value"></a>傳回值  
 游標影像控制代碼。 如果先前不指定的任何資料指標，則為 NULL。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="geticon"></a>  CButton::GetIcon  
 呼叫此成員函式取得的圖示，使用先前設定的控制代碼[SetIcon](#seticon)，也就是與按鈕相關聯。  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>傳回值  
 圖示控制代碼。 如果先前不指定的任何圖示，則為 NULL。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="getidealsize"></a>  CButton::GetIdealSize  
 擷取的理想大小的按鈕控制項。  
  
```  
BOOL GetIdealSize(SIZE* psize);
```  
  
### <a name="parameters"></a>參數  
 *psize*  
 按鈕的目前大小的指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式會模擬 BCM_GETIDEALSIZE 訊息中所述[按鈕](https://msdn.microsoft.com/library/windows/desktop/bb775943)Windows SDK 的一部分。  
  
##  <a name="getimagelist"></a>  CButton::GetImageList  
 呼叫這個方法來取得映像清單，從 [按鈕] 控制項。  
  
```  
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>參數  
 *pbuttonImagelist*  
 影像清單的指標`CButton`物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式會模擬 BCM_GETIMAGELIST 訊息中所述[按鈕](https://msdn.microsoft.com/library/windows/desktop/bb775943)Windows SDK 的一部分。  
  
##  <a name="getnote"></a>  CButton::GetNote  
 擷取目前的命令連結控制項相關聯的附註文字。  
  
```  
CString GetNote() const;  
  
BOOL GetNote(
    LPTSTR lpszNote,   
    UINT* cchNote) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[out]*lpszNote*|呼叫端會負責配置和解除配置之緩衝區的指標。 如果傳回的值為 TRUE，緩衝區會包含與目前的命令連結控制項; 相關聯的註解文字否則，緩衝區是不變。|  
|[in、 out]*cchNote*|不帶正負號的整數變數的指標。<br /><br /> 呼叫這個方法時，變數會包含所指定的緩衝區的大小*lpszNote*參數。<br /><br /> 當這個方法傳回時，如果傳回的值為 TRUE 的變數會包含與目前的命令連結控制項相關聯的附註的大小。 如果傳回的值為 FALSE，則變數會包含包含附註所需的緩衝區大小。|  
  
### <a name="return-value"></a>傳回值  
 在第一個多載中， [CString](../../atl-mfc-shared/using-cstring.md)物件，其中包含與目前的命令連結控制項相關聯的註解文字。  
  
 -或-  
  
 在第二個多載中，則為 TRUE，如果這個方法會成功;否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於其按鈕樣式是 BS_COMMANDLINK 或 BS_DEFCOMMANDLINK 的控制項。  
  
 這個方法會傳送[BCM_GETNOTE](/windows/desktop/Controls/bcm-getnote)訊息，Windows SDK 中所述。  
  
##  <a name="getnotelength"></a>  CButton::GetNoteLength  
 擷取目前的命令連結控制項的註解文字的長度。  
  
```  
UINT GetNoteLength() const;  
```  
  
### <a name="return-value"></a>傳回值  
 附註文字，請在目前的命令連結控制項的 16 位元 Unicode 字元的長度。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於其按鈕樣式是 BS_COMMANDLINK 或 BS_DEFCOMMANDLINK 的控制項。  
  
 這個方法會傳送[BCM_GETNOTELENGTH](/windows/desktop/Controls/bcm-getnotelength)訊息，Windows SDK 中所述。  
  
##  <a name="getsplitglyph"></a>  CButton::GetSplitGlyph  
 擷取目前的分割按鈕控制項相關聯的圖像。  
  
```  
TCHAR GetSplitGlyph() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的分割按鈕控制項相關聯的圖像 （glyph） 字元。  
  
### <a name="remarks"></a>備註  
 圖像為特定字型字元的實體表示法。 分割按鈕控制項，例如可能附有圖像 （glyph） 的 Unicode 勾號字元 (U + 2713)。  
  
 這個方法只適用於其按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項。  
  
 這個方法會初始化`mask`隸屬[BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) BCSIF_GLYPH 旗標，然後傳送該結構的結構[BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo)訊息中所述Windows SDK。 當訊息函式傳回時，這個方法會擷取從字符`himlGlyph`結構成員。  
  
##  <a name="getsplitimagelist"></a>  CButton::GetSplitImageList  
 擷取[映像清單](../../mfc/reference/cimagelist-class.md)目前分割按鈕控制項。  
  
```  
CImageList* GetSplitImageList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)物件。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於其按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項。  
  
 這個方法會初始化`mask`隸屬[BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) BCSIF_IMAGE 旗標，然後傳送該結構的結構[BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo)訊息中所述Windows SDK。 當訊息函式傳回時，這個方法會擷取的映像清單`himlGlyph`結構成員。  
  
##  <a name="getsplitinfo"></a>  CButton::GetSplitInfo  
 擷取參數以決定 Windows 將目前的分割按鈕控制項的繪製。  
  
```  
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[out]*pInfo*|指標[BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo)接收目前的分割按鈕控制項的相關資訊的結構。 呼叫端會負責配置結構。|  
  
### <a name="return-value"></a>傳回值  
 如果成功，這個方法，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於其按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項。  
  
 這個方法會傳送[BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo)訊息，Windows SDK 中所述。  
  
##  <a name="getsplitsize"></a>  CButton::GetSplitSize  
 擷取目前的分割按鈕控制項的下拉式清單元件的週框矩形。  
  
```  
BOOL GetSplitSize(LPSIZE pSize) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[out]*pSize*|指標[大小](https://msdn.microsoft.com/library/windows/desktop/dd145106)接收之矩形的描述的結構。|  
  
### <a name="return-value"></a>傳回值  
 如果成功，這個方法，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於其按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項。  
  
 在展開分割按鈕控制項時，它可以顯示的下拉式清單元件，例如清單控制項或頁面巡覽區控制項。 這個方法會擷取包含下拉式清單元件的週框矩形。  
  
 這個方法會初始化`mask`隸屬[BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) BCSIF_SIZE 旗標，然後傳送該結構的結構[BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo)訊息中所述Windows SDK。 當訊息函式傳回時，這個方法會擷取從的周框`size`結構成員。  
  
##  <a name="getsplitstyle"></a>  CButton::GetSplitStyle  
 擷取定義目前的分割按鈕控制項的分割按鈕樣式。  
  
```  
UINT GetSplitStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 分割按鈕樣式的位元組合。 如需詳細資訊，請參閱 <<c0> `uSplitStyle` 隸屬[BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo)結構。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於其按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項。  
  
 分割按鈕樣式指定對齊方式、 外觀比例，以及與 Windows 繪製分割按鈕圖示的圖形化格式。  
  
 這個方法會初始化`mask`隸屬[BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) BCSIF_STYLE 旗標，然後傳送該結構的結構[BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo)訊息中所述Windows SDK。 當訊息函式傳回時，這個方法會擷取從分割按鈕樣式`uSplitStyle`結構成員。  
  
##  <a name="getstate"></a>  CButton::GetState  
 擷取按鈕控制項的狀態。  
  
```  
UINT GetState() const;  
```  
  
### <a name="return-value"></a>傳回值  
 位元欄位包含值，指出按鈕控制項的目前狀態的組合。 下表列出可能的值。  
  
|按鈕狀態|值|描述|  
|------------------|-----------|-----------------|  
|BST_UNCHECKED|0x0000|初始狀態。|  
|BST_CHECKED|0x0001|已選取按鈕控制項。|  
|BST_INDETERMINATE|0x0002|狀態為不定 （只有按鈕控制項有三種狀態時）。|  
|BST_PUSHED|0x0004|已按下按鈕控制項。|  
|BST_FOCUS|0x0008|按鈕控制項具有焦點。|  
  
### <a name="remarks"></a>備註  
 BS_3STATE 或 BS_AUTO3STATE 按鈕樣式的按鈕控制項，會建立名為不定狀態的第三個狀態的核取方塊。 不定狀態指出，核取方塊不是已核取或取消核取。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="gettextmargin"></a>  CButton::GetTextMargin  
 呼叫這個方法來取得文字邊界`CButton`物件。  
  
```  
BOOL GetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>參數  
 *pmargin*  
 指標文字邊界`CButton`物件。  
  
### <a name="return-value"></a>傳回值  
 傳回文字邊界。  
  
### <a name="remarks"></a>備註  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式會模擬 BCM_GETTEXTMARGIN 訊息中所述[按鈕](https://msdn.microsoft.com/library/windows/desktop/bb775943)Windows SDK 的一部分。  
  
##  <a name="setbitmap"></a>  CButton::SetBitmap  
 呼叫此成員函式，將新的點陣圖按鈕。  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>參數  
 *hBitmap*  
 點陣圖的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 先前與按鈕關聯的點陣圖的控制代碼。  
  
### <a name="remarks"></a>備註  
 點陣圖會自動放置按鈕，依預設置中對齊表面。 如果點陣圖按鈕太大，則會遭到裁剪任一邊。 您可以選擇其他的對齊方式選項，包括下列：  
  
- BS_TOP  
  
- BS_LEFT  
  
- BS_RIGHT  
  
- BS_CENTER  
  
- BS_BOTTOM  
  
- BS_VCENTER  
  
 不同於[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)，它會使用每個按鈕時，四個點陣圖`SetBitmap`會使用每個按鈕只能有一個點陣圖。 按下按鈕時，點陣圖會顯示向下和向右移位。  
  
 您必須負責釋放與它完成時的點陣圖。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="setbuttonstyle"></a>  CButton::SetButtonStyle  
 變更按鈕的樣式。  
  
```  
void SetButtonStyle(
    UINT nStyle,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *nStyle*  
 指定[按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。  
  
 *bRedraw*  
 指定是否要重新描繪按鈕。 非零值會重繪按鈕。 0 的值不會重新繪製按鈕。 根據預設，按鈕會重新繪製。  
  
### <a name="remarks"></a>備註  
 使用`GetButtonStyle`成員函式來擷取按鈕樣式。 的低序位字組的完成按鈕樣式是特定按鈕的樣式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="setcheck"></a>  CButton::SetCheck  
 設定或重設選項按鈕或核取方塊的核取狀態。  
  
```  
void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>參數  
 *n*  
 指定的核取狀態。 這個參數可以是下列其中一項：  
  
|值|意義|  
|-----------|-------------|  
|BST_UNCHECKED|按鈕狀態設定為未核取。|  
|BST_CHECKED|設定按鈕的狀態檢查。|  
|BST_INDETERMINATE|按鈕狀態設定為不定。 只有當按鈕的 BS_3STATE 或 BS_AUTO3STATE 樣式，可用此值。|  
  
### <a name="remarks"></a>備註  
 此成員函式沒有在按鈕上的任何作用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="setcursor"></a>  CButton::SetCursor  
 呼叫此成員函式，將新的資料指標關聯的按鈕。  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>參數  
 *hCursor*  
 資料指標控制代碼。  
  
### <a name="return-value"></a>傳回值  
 先前與按鈕關聯的資料指標控制代碼。  
  
### <a name="remarks"></a>備註  
 資料指標會自動放置按鈕，依預設置中對齊表面。 如果游標位於太大按鈕，則會遭到裁剪任一邊。 您可以選擇其他的對齊方式選項，包括下列：  
  
- BS_TOP  
  
- BS_LEFT  
  
- BS_RIGHT  
  
- BS_CENTER  
  
- BS_BOTTOM  
  
- BS_VCENTER  
  
 不同於[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)，它會使用每個按鈕時，四個點陣圖`SetCursor`使用每個按鈕只能有一個資料指標。 按下按鈕時，資料指標會顯示向下和向右移位。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="setdropdownstate"></a>  CButton::SetDropDownState  
 設定目前的分割按鈕控制項的下拉式清單狀態。  
  
```  
BOOL SetDropDownState(BOOL fDropDown);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*fDropDown*|True 表示要設定 BST_DROPDOWNPUSHED 檢視狀態。否則為 FALSE。|  
  
### <a name="return-value"></a>傳回值  
 如果成功，這個方法，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 分割按鈕控制項具有 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 樣式，且包含按鈕和其右邊的下拉式箭號。 如需詳細資訊，請參閱 <<c0> [ 按鈕樣式](/windows/desktop/Controls/button-styles)。 通常，使用者按一下下拉箭號時，會設定下拉式清單的狀態。 使用此方法以程式設計方式設定下拉式清單控制項的狀態。 向下箭頭繪製陰影來表示的狀態。  
  
 這個方法會傳送[BCM_SETDROPDOWNSTATE](/windows/desktop/Controls/bcm-setdropdownstate)訊息，Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數*m_splitButton*，也就是用來以程式設計方式存取分割按鈕控制項。 在下列範例會使用這個變數。  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定分割按鈕控制項，以指出下拉箭號會推入的狀態。  
  
 [!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]  
  
##  <a name="setelevationrequired"></a>  CButton::SetElevationRequired  
 設定目前的 [按鈕] 控制項以狀態`elevation required`，這是所需的控制項來顯示提高權限的安全性圖示。  
  
```  
BOOL SetElevationRequired(BOOL fElevationRequired);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*fElevationRequired*|True 會設定`elevation required`狀態; 否則為 FALSE。|  
  
### <a name="return-value"></a>傳回值  
 如果成功，這個方法，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 如果按鈕或命令連結控制項需要提高權限的安全性權限來執行動作，將控制項設為`elevation required`狀態。 接下來，Windows 會在控制項上顯示使用者帳戶控制 (UAC) 保護盾圖示。 詳細資訊，請參閱 「 使用者帳戶控制 」，網址[MSDN](http://go.microsoft.com/fwlink/p/?linkid=18507)。  
  
 這個方法會傳送[BCM_SETSHIELD](/windows/desktop/Controls/bcm-setshield)訊息，Windows SDK 中所述。  
  
##  <a name="seticon"></a>  CButton::SetIcon  
 呼叫此成員函式，將新的圖示與按鈕。  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>參數  
 *hIcon*  
 圖示的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 先前與按鈕關聯的圖示的控制代碼。  
  
### <a name="remarks"></a>備註  
 圖示會自動放置按鈕，依預設置中對齊表面。 如果圖示是太大按鈕，則會遭到裁剪任一邊。 您可以選擇其他的對齊方式選項，包括下列：  
  
- BS_TOP  
  
- BS_LEFT  
  
- BS_RIGHT  
  
- BS_CENTER  
  
- BS_BOTTOM  
  
- BS_VCENTER  
  
 不同於[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)，它會使用每個按鈕時，四個點陣圖`SetIcon`會使用每個按鈕只能有一個圖示。 按下按鈕時，圖示會顯示向下和向右移位。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="setimagelist"></a>  CButton::SetImageList  
 呼叫這個方法來設定影像清單的`CButton`物件。  
  
```  
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>參數  
 *pbuttonImagelist*  
 新的映像清單的指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗則為 FALSE。  
  
### <a name="remarks"></a>備註  
 此成員函式會模擬 BCM_SETIMAGELIST 訊息中所述[按鈕](https://msdn.microsoft.com/library/windows/desktop/bb775943)Windows SDK 的一部分。  
  
##  <a name="setnote"></a>  CButton::SetNote  
 設定目前的命令連結控制項的附註文字。  
  
```  
BOOL SetNote(LPCTSTR lpszNote);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*lpszNote*|已設定為命令連結控制項的註解文字的 Unicode 字串的指標。|  
  
### <a name="return-value"></a>傳回值  
 如果成功，這個方法，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於其按鈕樣式是 BS_COMMANDLINK 或 BS_DEFCOMMANDLINK 的控制項。  
  
 這個方法會傳送[BCM_SETNOTE](/windows/desktop/Controls/bcm-setnote)訊息，Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數*m_cmdLink*，也就是用來以程式設計方式存取 命令連結控制項。 在下列範例會使用這個變數。  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定命令連結控制項的附註文字。  
  
 [!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]  
  
##  <a name="setsplitglyph"></a>  CButton::SetSplitGlyph  
 將指定的圖像 （glyph） 與目前的分割按鈕控制項產生關聯。  
  
```  
BOOL SetSplitGlyph(TCHAR chGlyph);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*chGlyph*|指定要作為分割按鈕下拉式箭號圖像 （glyph） 的字元。|  
  
### <a name="return-value"></a>傳回值  
 如果成功，這個方法，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於具有 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 將按鈕樣式控制項。  
  
 圖像為特定字型字元的實體表示法。 *ChGlyph*參數不作為圖像 （glyph），但改為用來從系統定莪圖像 （glyph） 的一組選取圖像 （glyph）。 預設下拉箭號圖像 （glyph） 的字元 '6'，所指定，和類似的 Unicode 字元黑色向下三角形 (U + 25BC)。  
  
 這個方法會初始化`mask`隸屬[BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) BCSIF_GLYPH 旗標的結構和`himlGlyph`成員*chGlyph*參數，然後傳送，結構[BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) Windows SDK 中所述的訊息。  
  
##  <a name="setsplitimagelist"></a>  CButton::SetSplitImageList  
 將產生關聯[映像清單](../../mfc/reference/cimagelist-class.md)與目前的分割按鈕控制項。  
  
```  
BOOL SetSplitImageList(CImageList* pSplitImageList);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*pSplitImageList*|指標[CImageList](../../mfc/reference/cimagelist-class.md)来指派給目前的分割按鈕控制項的物件。|  
  
### <a name="return-value"></a>傳回值  
 如果成功，這個方法，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於其按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項。  
  
 這個方法會初始化`mask`隸屬[BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) BCSIF_IMAGE 旗標的結構和`himlGlyph`成員*pSplitImageList*參數，然後按一下 傳送在該結構[BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) Windows SDK 中所述的訊息。  
  
##  <a name="setsplitinfo"></a>  CButton::SetSplitInfo  
 指定參數以決定 Windows 將目前的分割按鈕控制項的繪製。  
  
```  
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*pInfo*|指標[BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo)結構，定義目前的分割按鈕控制項。|  
  
### <a name="return-value"></a>傳回值  
 如果成功，這個方法，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於其按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項。  
  
 這個方法會傳送[BCM_SETSPLITINFO](/windows/desktop/Controls/bcm-setsplitinfo)訊息，Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_splitButton`，也就是用來以程式設計方式存取分割按鈕控制項。  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會變更用來分割按鈕下拉式箭號圖像。 範例替代向上三角形圖像 （glyph） 的預設值向下三角形圖像 （glyph）。 會顯示圖像 （glyph） 取決於您在中指定的字元`himlGlyph`隸屬`BUTTON_SPLITINFO`結構。 向下三角形圖像 （glyph） 指定的字元 '6' 並向上三角形圖像 （glyph） 指定的字元' 5'。 相較之下，請參閱方法很方便[CButton::SetSplitGlyph](#setsplitglyph)。  
  
 [!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]  
  
##  <a name="setsplitsize"></a>  CButton::SetSplitSize  
 設定目前的分割按鈕控制項的下拉式清單元件的週框矩形。  
  
```  
BOOL SetSplitSize(LPSIZE pSize);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*pSize*|指標[大小](https://msdn.microsoft.com/library/windows/desktop/dd145106)該結構描述的周框。|  
  
### <a name="return-value"></a>傳回值  
 如果成功，這個方法，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於其按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項。  
  
 在展開分割按鈕控制項時，它可以顯示的下拉式清單元件，例如清單控制項或頁面巡覽區控制項。 這個方法會指定週框矩形包含下拉式清單元件的大小。  
  
 這個方法會初始化`mask`隸屬[BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) BCSIF_SIZE 旗標的結構和`size`成員*pSize*參數，然後按一下 傳送的結構在  [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) Windows SDK 中所述的訊息。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_splitButton`，也就是用來以程式設計方式存取分割按鈕控制項。 在下列範例會使用這個變數。  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會加倍大小分割按鈕下拉式箭號。  
  
 [!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]  
  
##  <a name="setsplitstyle"></a>  CButton::SetSplitStyle  
 設定目前的分割按鈕控制項的樣式。  
  
```  
BOOL SetSplitStyle(UINT uSplitStyle);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*uSplitStyle*|分割按鈕樣式的位元組合。 如需詳細資訊，請參閱 <<c0> `uSplitStyle` 隸屬[BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo)結構。|  
  
### <a name="return-value"></a>傳回值  
 如果成功，這個方法，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於其按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項。  
  
 分割按鈕樣式指定對齊方式、 外觀比例，以及與 Windows 繪製分割按鈕圖示的圖形化格式。 如需詳細資訊，請參閱 <<c0> `uSplitStyle` 隸屬[BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo)結構。  
  
 這個方法會初始化`mask`隸屬[BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) BCSIF_STYLE 旗標的結構和`uSplitStyle`成員*uSplitStyle*參數，然後傳送，結構[BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) Windows SDK 中所述的訊息。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_splitButton`，也就是用來以程式設計方式存取分割按鈕控制項。  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例設定分割按鈕下拉式箭頭的樣式。 BCSS_ALIGNLEFT 樣式顯示箭號按鈕，左側和 BCSS_STRETCH 樣式會保留下拉箭號的比例，當您調整 [] 按鈕。  
  
 [!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]  
  
##  <a name="setstate"></a>  CButton::SetState  
 設定反白顯示的按鈕控制項。  
  
```  
void SetState(BOOL bHighlight);
```  
  
### <a name="parameters"></a>參數  
 *bHighlight*  
 指定是否要反白顯示 按鈕。 反白顯示的按鈕，非零的值值 0 會移除任何反白顯示。  
  
### <a name="remarks"></a>備註  
 反白顯示會影響外部的按鈕控制項。 它沒有任何作用核取狀態的選項按鈕或核取方塊。  
  
 當使用者按一下，並保留左的滑鼠按鈕時自動反白顯示的按鈕控制項。 當使用者放開滑鼠按鈕時，會移除反白顯示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="settextmargin"></a>  CButton::SetTextMargin  
 呼叫此方法以設定的文字邊界`CButton`物件。  
  
```  
BOOL SetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>參數  
 *pmargin*  
 新的文字邊界指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗則為 FALSE。  
  
### <a name="remarks"></a>備註  
 此成員函式會模擬 BCM_SETTEXTMARGIN 訊息中所述[按鈕](https://msdn.microsoft.com/library/windows/desktop/bb775943)Windows SDK 的一部分。  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CComboBox 類別](../../mfc/reference/ccombobox-class.md)   
 [CEdit 類別](../../mfc/reference/cedit-class.md)   
 [CListBox 類別](../../mfc/reference/clistbox-class.md)   
 [CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)   
 [CStatic 類別](../../mfc/reference/cstatic-class.md)   
 [CBitmapButton 類別](../../mfc/reference/cbitmapbutton-class.md)   
 [CDialog 類別](../../mfc/reference/cdialog-class.md)
