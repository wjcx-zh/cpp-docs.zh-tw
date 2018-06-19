---
title: CMFCRibbonEdit 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CopyFrom
- AFXRIBBONEDIT/CMFCRibbonEdit::CreateEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::DestroyCtrl
- AFXRIBBONEDIT/CMFCRibbonEdit::DropDownList
- AFXRIBBONEDIT/CMFCRibbonEdit::EnableSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::GetCompactSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::GetIntermediateSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::GetWidth
- AFXRIBBONEDIT/CMFCRibbonEdit::HasCompactMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasFocus
- AFXRIBBONEDIT/CMFCRibbonEdit::HasLargeMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::IsHighlighted
- AFXRIBBONEDIT/CMFCRibbonEdit::OnAfterChangeRect
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDraw
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawLabelAndImage
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawOnList
- AFXRIBBONEDIT/CMFCRibbonEdit::OnEnable
- AFXRIBBONEDIT/CMFCRibbonEdit::OnHighlight
- AFXRIBBONEDIT/CMFCRibbonEdit::OnKey
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonDown
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonUp
- AFXRIBBONEDIT/CMFCRibbonEdit::OnRTLChanged
- AFXRIBBONEDIT/CMFCRibbonEdit::OnShow
- AFXRIBBONEDIT/CMFCRibbonEdit::Redraw
- AFXRIBBONEDIT/CMFCRibbonEdit::SetACCData
- AFXRIBBONEDIT/CMFCRibbonEdit::SetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::SetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::SetWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CanBeStretched
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CopyFrom
- CMFCRibbonEdit [MFC], CreateEdit
- CMFCRibbonEdit [MFC], DestroyCtrl
- CMFCRibbonEdit [MFC], DropDownList
- CMFCRibbonEdit [MFC], EnableSpinButtons
- CMFCRibbonEdit [MFC], GetCompactSize
- CMFCRibbonEdit [MFC], GetEditText
- CMFCRibbonEdit [MFC], GetIntermediateSize
- CMFCRibbonEdit [MFC], GetTextAlign
- CMFCRibbonEdit [MFC], GetWidth
- CMFCRibbonEdit [MFC], HasCompactMode
- CMFCRibbonEdit [MFC], HasFocus
- CMFCRibbonEdit [MFC], HasLargeMode
- CMFCRibbonEdit [MFC], HasSpinButtons
- CMFCRibbonEdit [MFC], IsHighlighted
- CMFCRibbonEdit [MFC], OnAfterChangeRect
- CMFCRibbonEdit [MFC], OnDraw
- CMFCRibbonEdit [MFC], OnDrawLabelAndImage
- CMFCRibbonEdit [MFC], OnDrawOnList
- CMFCRibbonEdit [MFC], OnEnable
- CMFCRibbonEdit [MFC], OnHighlight
- CMFCRibbonEdit [MFC], OnKey
- CMFCRibbonEdit [MFC], OnLButtonDown
- CMFCRibbonEdit [MFC], OnLButtonUp
- CMFCRibbonEdit [MFC], OnRTLChanged
- CMFCRibbonEdit [MFC], OnShow
- CMFCRibbonEdit [MFC], Redraw
- CMFCRibbonEdit [MFC], SetACCData
- CMFCRibbonEdit [MFC], SetEditText
- CMFCRibbonEdit [MFC], SetTextAlign
- CMFCRibbonEdit [MFC], SetWidth
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: daa6a5976f4f20ba067eed047a4ff83b30550ea9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374172"
---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit 類別
實作編輯控制項放在功能區列上。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonEdit : public CMFCRibbonButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|建構 `CMFCRibbonEdit` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|指出是否的高度`CMFCRibbonEdit`控制項可以以垂直方式增加至功能區列的高度。|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|建構 `CMFCRibbonEdit` 物件。|  
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|複製指定的狀態`CMFCRibbonEdit`物件與目前`CMFCRibbonEdit`物件。|  
|[CMFCRibbonEdit::CreateEdit](#createedit)|建立新的文字方塊，用於`CMFCRibbonEdit`物件。|  
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|終結`CMFCRibbonEdit`物件。|  
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|下拉清單方塊。|  
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|啟用並設定微調按鈕的文字方塊中的範圍。|  
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|擷取的壓縮大小`CFMCRibbonEdit`物件。|  
|[CMFCRibbonEdit::GetEditText](#getedittext)|擷取在文字方塊中的文字。|  
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|擷取的中繼大小`CMFCRibbonEdit`物件。|  
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|擷取在文字方塊中文字的對齊方式。|  
|[CMFCRibbonEdit::GetWidth](#getwidth)|擷取的寬度，以像素的`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|指出是否顯示大小`CMFCRibbonEdit`控制項可以壓縮。|  
|[CMFCRibbonEdit::HasFocus](#hasfocus)|指出是否`CMFCRIbbonEdit`控制項有焦點。|  
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|指出是否顯示大小`CMFCRibbonEdit`控制項都可以是大型。|  
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|指出文字方塊是否有微調按鈕。|  
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|指出是否`CMFCRibbonEdit`反白顯示控制項。|  
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|由架構呼叫時的顯示矩形的尺寸`CMFCRibbonEdit`控制的變更。|  
|[CMFCRibbonEdit::OnDraw](#ondraw)|由架構呼叫以繪製`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|由架構呼叫以繪製在標籤和影像的`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|由架構呼叫以繪製`CMFCRibbonEdit`命令清單方塊中的控制項。|  
|[CMFCRibbonEdit::OnEnable](#onenable)|由架構呼叫以啟用或停用`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|當滑鼠指標進入或離開範圍時，由架構呼叫`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::OnKey](#onkey)|當使用者按下 keytip 時由架構呼叫和`CMFCRibbonEdit`控制項有焦點。|  
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|由架構呼叫以更新`CMFCRibbonEdit`控制當使用者按下滑鼠左的按鈕控制項上。|  
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|當使用者放開滑鼠左的按鈕時由架構呼叫。|  
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|由架構呼叫以更新`CMFCRibbonEdit`控制當版面配置變更方向。|  
|[CMFCRibbonEdit::OnShow](#onshow)|由架構呼叫以顯示或隱藏`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::Redraw](#redraw)|更新的顯示`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::SetACCData](#setaccdata)|設定的協助工具資料`CMFCRibbonEdit`物件。|  
|[CMFCRibbonEdit::SetEditText](#setedittext)|在文字方塊中設定的文字。|  
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|設定文字方塊的文字對齊方式。|  
|[CMFCRibbonEdit::SetWidth](#setwidth)|設定文字方塊的寬度`CMFCRibbonEdit`控制項。|  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例示範如何建構`CMFCRibbonEdit`物件、 顯示微調按鈕旁的編輯控制項，並將文字編輯控制項的設定。 此程式碼片段是部分[MS Office 2007 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭：** afxRibbonEdit.h  
  
##  <a name="canbestretched"></a>  CMFCRibbonEdit::CanBeStretched  
 指出是否的高度[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項可以以垂直方式增加至功能區列的高度。  
  
```  
virtual BOOL CanBeStretched();
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="cmfcribbonedit"></a>  CMFCRibbonEdit::CMFCRibbonEdit  
 建構[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。  
  
```  
CMFCRibbonEdit(
    UINT nID,  
    int nWidth,  
    LPCTSTR lpszLabel = NULL,  
    int nImage = -1);

CMFCRibbonEdit();
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nID`  
 命令 ID 的`CMFCRibbonEdit`控制項。  
  
 [輸入] `nWidth`  
 寬度，單位為像素的文字方塊`CMFCRibbonEdit`控制項。  
  
 [輸入] `lpszLabel`  
 標籤`CMFCRibbonEdit`控制項。  
  
 [輸入] `nImage`  
 用於索引的小型影像`CMFCRibbonEdit`控制項。 使用的小型影像集合是由父功能區分類維護。  
  
### <a name="remarks"></a>備註  
 `CMFCRibbonEdit`控制項不會使用大型影像。  
  
##  <a name="copyfrom"></a>  CMFCRibbonEdit::CopyFrom  
 複製指定的狀態[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件與目前[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `src`  
 來源 `CMFCRibbonEdit` 物件。  
  
### <a name="remarks"></a>備註  
 `src`參數必須是型別`CMFCRibbonEdit`。  
  
##  <a name="createedit"></a>  CMFCRibbonEdit::CreateEdit  
 建立新的文字方塊，用於[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。  
  
```  
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWndParent`  
 父視窗的指標`CMFCRibbonEdit`物件。  
  
 [輸入] `dwEditStyle`  
 指定文字方塊的樣式。 您可以結合會在 < 備註 > 一節中所列出的視窗樣式[編輯控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775464)Windows SDK 中加以討論。  
  
### <a name="return-value"></a>傳回值  
 指向新的文字方塊中如果該方法成功。否則， `NULL`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生類別來建立自訂的文字方塊中。  
  
 您可以套用下列[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的文字方塊：  
  
- **WS_CHILD**  
  
- **WS_VISIBLE**  
  
- **WS_DISABLED**  
  
- **WS_GROUP**  
  
- **WS_TABSTOP**  
  
##  <a name="destroyctrl"></a>  CMFCRibbonEdit::DestroyCtrl  
 終結[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。  
  
```  
virtual void DestroyCtrl();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="dropdownlist"></a>  CMFCRibbonEdit::DropDownList  
 下拉清單方塊。  
  
```  
virtual void DropDownList();
```  
  
### <a name="remarks"></a>備註  
 依預設這個方法沒有任何作用。 覆寫此方法下拉式清單方塊。  
  
##  <a name="enablespinbuttons"></a>  CMFCRibbonEdit::EnableSpinButtons  
 啟用並設定微調按鈕的文字方塊中的範圍。  
  
```  
void EnableSpinButtons(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nMin`  
 微調按鈕的最小的值。  
  
 [輸入] `nMax`  
 微調按鈕的最大值。  
  
### <a name="remarks"></a>備註  
 微調按鈕顯示向上和向下箭號，並讓使用者移動一組固定的值。  
  
##  <a name="getcompactsize"></a>  CMFCRibbonEdit::GetCompactSize  
 擷取的壓縮大小[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標`CMFCRibbonEdit`物件。  
  
### <a name="return-value"></a>傳回值  
 目的壓縮大小`CMFCRibbonEdit`物件。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getedittext"></a>  CMFCRibbonEdit::GetEditText  
 擷取在文字方塊中的文字。  
  
```  
CString GetEditText() const;  
```  
  
### <a name="return-value"></a>傳回值  
 [文字] 方塊中的文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getintermediatesize"></a>  CMFCRibbonEdit::GetIntermediateSize  
 擷取的中繼大小[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標`CMFCRibbonEdit`物件。  
  
### <a name="return-value"></a>傳回值  
 中繼大小`CMFCRibbonEdit`物件。  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettextalign"></a>  CMFCRibbonEdit::GetTextAlign  
 擷取在文字方塊中文字的對齊方式。  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>傳回值  
 文字對齊方式列舉值。 請參閱 < 備註 > 一節提供可能的值。  
  
### <a name="remarks"></a>備註  
 傳回的值可以是下列的編輯控制項樣式的其中一個：  
  
- **ES_LEFT**為靠左對齊  
  
- **ES_CENTER**的置中對齊  
  
- **ES_RIGHT**為靠右對齊  
  
 如需有關這些樣式的詳細資訊，請參閱[編輯控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775464)。  
  
##  <a name="getwidth"></a>  CMFCRibbonEdit::GetWidth  
 擷取的寬度，以像素的[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
int GetWidth(BOOL bInFloatyMode = FALSE) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bInFloatyMode`  
 `TRUE` 如果`CMFCRibbonEdit`控制項為浮動的模式; 否則`FALSE`。  
  
### <a name="return-value"></a>傳回值  
 寬度，以像素的`CMFCRibbonEdit`控制項。  
  
### <a name="remarks"></a>備註  
  
##  <a name="hascompactmode"></a>  CMFCRibbonEdit::HasCompactMode  
 指出是否顯示大小[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項可以壓縮。  
  
```  
virtual BOOL HasCompactMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
 依預設這個方法一律會傳回`TRUE`。 覆寫此方法，指出是否可壓縮的顯示大小。  
  
##  <a name="hasfocus"></a>  CMFCRibbonEdit::HasFocus  
 指出是否[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項有焦點。  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果`CMFCRibbonEdit`控制項有焦點; 否則為`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="haslargemode"></a>  CMFCRibbonEdit::HasLargeMode  
 指出是否顯示大小[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項都可以是大型。  
  
```  
virtual BOOL HasLargeMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 依預設這個方法一律會傳回`FALSE`。 覆寫此方法，指出是否顯示大小可能會大。  
  
##  <a name="hasspinbuttons"></a>  CMFCRibbonEdit::HasSpinButtons  
 指出文字方塊是否有微調按鈕。  
  
```  
virtual BOOL HasSpinButtons() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果文字方塊具有微調按鈕。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ishighlighted"></a>  CMFCRibbonEdit::IsHighlighted  
 指出是否[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)反白顯示控制項。  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果`CMFCRibbonEdit`控制項已反白顯示，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onafterchangerect"></a>  CMFCRibbonEdit::OnAfterChangeRect  
 由架構呼叫時的顯示矩形的尺寸[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制變更。  
  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標`CMFCRibbonEdit`控制項。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondraw"></a>  CMFCRibbonEdit::OnDraw  
 由架構呼叫以繪製[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標`CMFCRibbonEdit`控制項。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawlabelandimage"></a>  CMFCRibbonEdit::OnDrawLabelAndImage  
 由架構呼叫以繪製在標籤和影像的[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
virtual void OnDrawLabelAndImage(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標`CMFCRibbonEdit`控制項。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawonlist"></a>  CMFCRibbonEdit::OnDrawOnList  
 由架構呼叫以繪製[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)命令清單方塊中的控制項。  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標`CMFCRibbonEdit`控制項。  
  
 [輸入] `strText`  
 顯示文字[ ] (../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit 類別")。  
  
 [輸入] `nTextOffset`  
 像素為單位，從清單方塊來顯示文字的左邊算起的距離。  
  
 [輸入] `rect`  
 顯示矩形`CMFCRibbonEdit`控制項。  
  
 [輸入] `bIsSelected`  
 不使用這個參數。  
  
 [輸入] `bHighlighted`  
 不使用這個參數。  
  
### <a name="remarks"></a>備註  
 命令清單方塊會顯示功能區控制項，讓使用者可以自訂快速存取工具列。  
  
##  <a name="onenable"></a>  CMFCRibbonEdit::OnEnable  
 由架構呼叫以啟用或停用[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
virtual void OnEnable(BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bEnable`  
 `TRUE` 若要啟用控制項。`FALSE`停用控制項。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onhighlight"></a>  CMFCRibbonEdit::OnHighlight  
 當滑鼠指標進入或離開範圍時，由架構呼叫[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
virtual void OnHighlight(BOOL bHighlight);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bHighlight`  
 `TRUE` 如果在指標位於界限`CMFCRibbonEdit`控制項等控制項，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onkey"></a>  CMFCRibbonEdit::OnKey  
 當使用者按下 keytip 時由架構呼叫和[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項有焦點。  
  
```  
virtual BOOL OnKey(BOOL bIsMenuKey);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bIsMenuKey`  
 `TRUE` 如果 keytip 顯示快顯功能表。否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 如果事件已處理，則為 `TRUE`；否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onlbuttondown"></a>  CMFCRibbonEdit::OnLButtonDown  
 由架構呼叫以更新[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制當使用者按下滑鼠左的按鈕控制項上。  
  
```  
virtual void OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `point`  
 不使用這個參數。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onlbuttonup"></a>  CMFCRibbonEdit::OnLButtonUp  
 當使用者放開滑鼠左的按鈕時由架構呼叫。  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `point`  
 不使用這個參數。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onrtlchanged"></a>  CMFCRibbonEdit::OnRTLChanged  
 由架構呼叫以更新[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制當版面配置變更方向。  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bIsRTL`  
 `TRUE` 如果配置為從右至左。`FALSE`如果版面配置是由左到右。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onshow"></a>  CMFCRibbonEdit::OnShow  
 由架構呼叫以顯示或隱藏[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bShow`  
 `TRUE` 若要顯示的控制項。`FALSE`隱藏控制項。  
  
### <a name="remarks"></a>備註  
  
##  <a name="redraw"></a>  CMFCRibbonEdit::Redraw  
 更新的顯示[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
virtual void Redraw();
```  
  
### <a name="remarks"></a>備註  
 這個方法會重新繪製的顯示矩形`CMFCRibbonEdit`透過間接呼叫[CWnd::RedrawWindow](http://msdn.microsoft.com/library/windows/desktop/dd162911)與`RDW_INVALIDATE`， `RDW_ERASE`，和`RDW_UPDATENOW`旗標集。  
  
##  <a name="setaccdata"></a>  CMFCRibbonEdit::SetACCData  
 設定的協助工具資料[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>參數  
 `pParent`  
 指標的父視窗`CMFCRibbonEdit`物件。  
  
 `data`  
 協助工具資料`CMFCRibbonEdit`物件。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setedittext"></a>  CMFCRibbonEdit::SetEditText  
 在文字方塊中設定的文字。  
  
```  
void SetEditText(CString strText);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `strText`  
 文字方塊的文字。  
  
##  <a name="settextalign"></a>  CMFCRibbonEdit::SetTextAlign  
 設定文字方塊的文字對齊方式。  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nAlign`  
 文字對齊方式列舉值。 請參閱 < 備註 > 一節提供可能的值。  
  
### <a name="remarks"></a>備註  
 參數`nAlign`是其中一個下編輯控制項樣式：  
  
- **ES_LEFT**為靠左對齊  
  
- **ES_CENTER**的置中對齊  
  
- **ES_RIGHT**為靠右對齊  
  
 如需有關這些樣式的詳細資訊，請參閱[編輯控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775464)。  
  
##  <a name="setwidth"></a>  CMFCRibbonEdit::SetWidth  
 設定文字方塊的寬度[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
void SetWidth(
    int nWidth,  
    BOOL bInFloatyMode = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nWidth`  
 寬度 （以像素的文字方塊）。  
  
 `bInFloatyMode`  
 `TRUE` 設定浮點模式; 寬度`FALSE`設定的一般模式的寬度。  
  
### <a name="remarks"></a>備註  
 `CMFCRibbonEdit`控制項有兩種寬度根據它的顯示模式： 浮點模式和標準模式。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)