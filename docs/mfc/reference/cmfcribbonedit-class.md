---
title: "CMFCRibbonEdit 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
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
- CMFCRibbonEdit class
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
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
ms.openlocfilehash: 03eb96bf971b53a2100e6f93bac2f0641f0298e1
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit 類別
實作編輯控制項，位在功能區列上。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonEdit : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|建構 `CMFCRibbonEdit` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|指出是否高度`CMFCRibbonEdit`控制項可以以垂直方式增加到功能區列的高度。|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|建構 `CMFCRibbonEdit` 物件。|  
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|複製指定的狀態`CMFCRibbonEdit`物件與目前`CMFCRibbonEdit`物件。|  
|[CMFCRibbonEdit::CreateEdit](#createedit)|建立新的文字方塊中，如`CMFCRibbonEdit`物件。|  
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|終結`CMFCRibbonEdit`物件。|  
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|下拉清單方塊。|  
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|啟用並設定文字方塊的微調按鈕的範圍。|  
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|擷取的壓縮大小`CFMCRibbonEdit`物件。|  
|[CMFCRibbonEdit::GetEditText](#getedittext)|擷取在文字方塊中的文字。|  
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|擷取的中繼大小`CMFCRibbonEdit`物件。|  
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|擷取在文字方塊中文字的對齊方式。|  
|[CMFCRibbonEdit::GetWidth](#getwidth)|擷取的寬度，單位為像素的`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|指出是否顯示大小為`CMFCRibbonEdit`控制項可以壓縮。|  
|[CMFCRibbonEdit::HasFocus](#hasfocus)|指出是否`CMFCRIbbonEdit`控制項取得焦點。|  
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|指出是否顯示大小為`CMFCRibbonEdit`控制項可能很大。|  
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|指出文字方塊是否有微調按鈕。|  
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|指出是否`CMFCRibbonEdit`控制會反白顯示。|  
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|由架構呼叫時的顯示矩形的尺寸`CMFCRibbonEdit`控制的變更。|  
|[CMFCRibbonEdit::OnDraw](#ondraw)|要繪製架構呼叫`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|若要繪製標籤和映像的架構所呼叫`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|要繪製架構呼叫`CMFCRibbonEdit`命令的清單方塊中的控制項。|  
|[CMFCRibbonEdit::OnEnable](#onenable)|若要啟用或停用架構呼叫`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|當滑鼠指標進入或離開範圍時，由框架呼叫`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::OnKey](#onkey)|當使用者按下 keytip，由框架呼叫和`CMFCRibbonEdit`控制項取得焦點。|  
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|更新架構呼叫`CMFCRibbonEdit`控制當使用者在控制項上按滑鼠左鍵時。|  
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|當使用者放開滑鼠左鍵時，由架構呼叫。|  
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|更新架構呼叫`CMFCRibbonEdit`控制版面配置方向的變更時。|  
|[CMFCRibbonEdit::OnShow](#onshow)|若要顯示或隱藏架構呼叫`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::Redraw](#redraw)|更新的顯示`CMFCRibbonEdit`控制項。|  
|[CMFCRibbonEdit::SetACCData](#setaccdata)|設定協助工具資料`CMFCRibbonEdit`物件。|  
|[CMFCRibbonEdit::SetEditText](#setedittext)|在文字方塊中設定的文字。|  
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|設定文字方塊的文字對齊方式。|  
|[CMFCRibbonEdit::SetWidth](#setwidth)|設定文字方塊的寬度`CMFCRibbonEdit`控制項。|  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例示範如何建構`CMFCRibbonEdit`物件、 顯示編輯控制 旁邊的微調按鈕，並將編輯控制項的文字。 此程式碼片段是一部分[MS Office 2007 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo #&7;](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxRibbonEdit.h  
  
##  <a name="canbestretched"></a>CMFCRibbonEdit::CanBeStretched  
 指出是否高度[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項可以以垂直方式增加到功能區列的高度。  
  
```  
virtual BOOL CanBeStretched();
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="cmfcribbonedit"></a>CMFCRibbonEdit::CMFCRibbonEdit  
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
 [in] `nID`  
 命令 ID 的`CMFCRibbonEdit`控制項。  
  
 [in] `nWidth`  
 寬度，單位為像素的文字方塊中`CMFCRibbonEdit`控制項。  
  
 [in] `lpszLabel`  
 標籤`CMFCRibbonEdit`控制項。  
  
 [in] `nImage`  
 要用於小影像的索引`CMFCRibbonEdit`控制項。 由父功能區類別負責維護的小型影像集合。  
  
### <a name="remarks"></a>備註  
 `CMFCRibbonEdit`控制項不會使用大影像。  
  
##  <a name="copyfrom"></a>CMFCRibbonEdit::CopyFrom  
 複製指定的狀態[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件與目前[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>參數  
 [in] `src`  
 來源 `CMFCRibbonEdit` 物件。  
  
### <a name="remarks"></a>備註  
 `src`參數必須是型別`CMFCRibbonEdit`。  
  
##  <a name="createedit"></a>CMFCRibbonEdit::CreateEdit  
 建立新的文字方塊中，如[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。  
  
```  
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndParent`  
 父視窗的指標`CMFCRibbonEdit`物件。  
  
 [in] `dwEditStyle`  
 指定文字方塊的樣式。 您可以結合 < 備註 > 一節中列出的視窗樣式[編輯控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775464)Windows SDK 中加以討論。  
  
### <a name="return-value"></a>傳回值  
 指向新的文字方塊中如果方法成功。否則， `NULL`。  
  
### <a name="remarks"></a>備註  
 在衍生類別來建立自訂的文字方塊中，這個方法會覆寫。  
  
 您可以套用下列[視窗樣式](../../mfc/reference/window-styles.md)的文字方塊中︰  
  
- **WS_CHILD**  
  
- **WS_VISIBLE**  
  
- **WS_DISABLED**  
  
- **WS_GROUP**  
  
- **WS_TABSTOP**  
  
##  <a name="destroyctrl"></a>CMFCRibbonEdit::DestroyCtrl  
 終結[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。  
  
```  
virtual void DestroyCtrl();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="dropdownlist"></a>CMFCRibbonEdit::DropDownList  
 下拉清單方塊。  
  
```  
virtual void DropDownList();
```  
  
### <a name="remarks"></a>備註  
 依預設這個方法沒有作用。 覆寫這個方法，以下拉式清單方塊。  
  
##  <a name="enablespinbuttons"></a>CMFCRibbonEdit::EnableSpinButtons  
 啟用並設定文字方塊的微調按鈕的範圍。  
  
```  
void EnableSpinButtons(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>參數  
 [in] `nMin`  
 微調按鈕的最小值。  
  
 [in] `nMax`  
 微調按鈕的最大值。  
  
### <a name="remarks"></a>備註  
 微調按鈕顯示向上和向下箭號，並讓使用者移動一組固定的值。  
  
##  <a name="getcompactsize"></a>CMFCRibbonEdit::GetCompactSize  
 擷取的壓縮大小[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容指標`CMFCRibbonEdit`物件。  
  
### <a name="return-value"></a>傳回值  
 壓縮大小`CMFCRibbonEdit`物件。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getedittext"></a>CMFCRibbonEdit::GetEditText  
 擷取在文字方塊中的文字。  
  
```  
CString GetEditText() const;  
```  
  
### <a name="return-value"></a>傳回值  
 [文字] 方塊中的文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getintermediatesize"></a>CMFCRibbonEdit::GetIntermediateSize  
 擷取的中繼大小[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容指標`CMFCRibbonEdit`物件。  
  
### <a name="return-value"></a>傳回值  
 中繼大小`CMFCRibbonEdit`物件。  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettextalign"></a>CMFCRibbonEdit::GetTextAlign  
 擷取在文字方塊中文字的對齊方式。  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>傳回值  
 文字對齊方式列舉值。 請參閱 < 備註 > 一節，取得可能的值。  
  
### <a name="remarks"></a>備註  
 傳回的值可以是下列的編輯控制項樣式的其中一個︰  
  
- **ES_LEFT**為靠左對齊  
  
- **ES_CENTER**的置中對齊  
  
- **ES_RIGHT**為靠右對齊  
  
 如需有關這些樣式的詳細資訊，請參閱[編輯控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775464)。  
  
##  <a name="getwidth"></a>CMFCRibbonEdit::GetWidth  
 擷取的寬度，單位為像素的[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
int GetWidth(BOOL bInFloatyMode = FALSE) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `bInFloatyMode`  
 `TRUE`如果`CMFCRibbonEdit`控制項處於浮動模式; 否則`FALSE`。  
  
### <a name="return-value"></a>傳回值  
 寬度，單位為像素的`CMFCRibbonEdit`控制項。  
  
### <a name="remarks"></a>備註  
  
##  <a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode  
 指出是否顯示大小的[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項可以壓縮。  
  
```  
virtual BOOL HasCompactMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
 依預設此方法一律傳回`TRUE`。 覆寫這個方法，指出是否可壓縮的顯示大小。  
  
##  <a name="hasfocus"></a>CMFCRibbonEdit::HasFocus  
 指出是否[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項取得焦點。  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`CMFCRibbonEdit`控制項取得焦點，否則為`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode  
 指出是否顯示大小的[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項可能很大。  
  
```  
virtual BOOL HasLargeMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 依預設此方法一律傳回`FALSE`。 覆寫這個方法，指出是否顯示大小可能會大。  
  
##  <a name="hasspinbuttons"></a>CMFCRibbonEdit::HasSpinButtons  
 指出文字方塊是否有微調按鈕。  
  
```  
virtual BOOL HasSpinButtons() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果文字方塊具有微調按鈕。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ishighlighted"></a>CMFCRibbonEdit::IsHighlighted  
 指出是否[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制會反白顯示。  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`CMFCRibbonEdit`控制項就會反白顯示，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect  
 由架構呼叫時的顯示矩形的尺寸[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制變更。  
  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容指標`CMFCRibbonEdit`控制項。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondraw"></a>CMFCRibbonEdit::OnDraw  
 要繪製架構呼叫[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容指標`CMFCRibbonEdit`控制項。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage  
 若要繪製標籤和映像的架構所呼叫[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
virtual void OnDrawLabelAndImage(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容指標`CMFCRibbonEdit`控制項。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawonlist"></a>CMFCRibbonEdit::OnDrawOnList  
 要繪製架構呼叫[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)命令的清單方塊中的控制項。  
  
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
 [in] `pDC`  
 裝置內容指標`CMFCRibbonEdit`控制項。  
  
 [in] `strText`  
 顯示文字[ ](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit class")。  
  
 [in] `nTextOffset`  
 像素為單位，從清單方塊來顯示文字的左邊算起的距離。  
  
 [in] `rect`  
 顯示矩形`CMFCRibbonEdit`控制項。  
  
 [in] `bIsSelected`  
 不使用這個參數。  
  
 [in] `bHighlighted`  
 不使用這個參數。  
  
### <a name="remarks"></a>備註  
 命令的清單方塊會顯示功能區控制項，讓使用者可以自訂快速存取工具列。  
  
##  <a name="onenable"></a>CMFCRibbonEdit::OnEnable  
 若要啟用或停用架構呼叫[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
virtual void OnEnable(BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用控制項。`FALSE`停用控制項。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onhighlight"></a>CMFCRibbonEdit::OnHighlight  
 當滑鼠指標進入或離開範圍時，由框架呼叫[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
virtual void OnHighlight(BOOL bHighlight);
```  
  
### <a name="parameters"></a>參數  
 [in] `bHighlight`  
 `TRUE`如果指標是在界限內的`CMFCRibbonEdit`控制項等控制項，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onkey"></a>CMFCRibbonEdit::OnKey  
 當使用者按下 keytip，由框架呼叫和[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項取得焦點。  
  
```  
virtual BOOL OnKey(BOOL bIsMenuKey);
```  
  
### <a name="parameters"></a>參數  
 [in] `bIsMenuKey`  
 `TRUE`如果 keytip 顯示快顯功能表。否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 如果事件已處理，則為 `TRUE`；否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onlbuttondown"></a>CMFCRibbonEdit::OnLButtonDown  
 更新架構呼叫[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制當使用者在控制項上按滑鼠左鍵時。  
  
```  
virtual void OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 不使用這個參數。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp  
 當使用者放開滑鼠左鍵時，由架構呼叫。  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 不使用這個參數。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onrtlchanged"></a>CMFCRibbonEdit::OnRTLChanged  
 更新架構呼叫[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制版面配置方向的變更時。  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>參數  
 [in] `bIsRTL`  
 `TRUE`如果版面配置是從右至左。`FALSE`如果版面配置是由左到右。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onshow"></a>CMFCRibbonEdit::OnShow  
 若要顯示或隱藏架構呼叫[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 [in] `bShow`  
 `TRUE`若要顯示的控制項。`FALSE`隱藏控制項。  
  
### <a name="remarks"></a>備註  
  
##  <a name="redraw"></a>CMFCRibbonEdit::Redraw  
 更新的顯示[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
virtual void Redraw();
```  
  
### <a name="remarks"></a>備註  
 這個方法會重新繪製的顯示矩形`CMFCRibbonEdit`透過間接呼叫[CWnd::RedrawWindow](http://msdn.microsoft.com/library/windows/desktop/dd162911)與`RDW_INVALIDATE`， `RDW_ERASE`，和`RDW_UPDATENOW`旗標集。  
  
##  <a name="setaccdata"></a>CMFCRibbonEdit::SetACCData  
 設定協助工具資料[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。  
  
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
  
##  <a name="setedittext"></a>CMFCRibbonEdit::SetEditText  
 在文字方塊中設定的文字。  
  
```  
void SetEditText(CString strText);
```  
  
### <a name="parameters"></a>參數  
 [in] `strText`  
 文字方塊的文字。  
  
##  <a name="settextalign"></a>CMFCRibbonEdit::SetTextAlign  
 設定文字方塊的文字對齊方式。  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>參數  
 [in] `nAlign`  
 文字對齊方式列舉值。 請參閱 < 備註 > 一節，取得可能的值。  
  
### <a name="remarks"></a>備註  
 參數`nAlign`是其中一個下列編輯控制項的樣式︰  
  
- **ES_LEFT**為靠左對齊  
  
- **ES_CENTER**的置中對齊  
  
- **ES_RIGHT**為靠右對齊  
  
 如需有關這些樣式的詳細資訊，請參閱[編輯控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775464)。  
  
##  <a name="setwidth"></a>CMFCRibbonEdit::SetWidth  
 設定文字方塊的寬度[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。  
  
```  
void SetWidth(
    int nWidth,  
    BOOL bInFloatyMode = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `nWidth`  
 寬度，單位為像素的文字方塊。  
  
 `bInFloatyMode`  
 `TRUE`若要設定浮動模式; 顯示的寬度`FALSE`設定標準模式的寬度。  
  
### <a name="remarks"></a>備註  
 `CMFCRibbonEdit`控制項有兩個的寬度，根據它的顯示模式︰ 浮點模式和標準模式。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)
