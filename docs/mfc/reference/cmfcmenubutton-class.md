---
title: CMFCMenuButton 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
dev_langs:
- C++
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d611acb34d4159abb41ffa333b4b2cfb6d94442
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton 類別
顯示快顯功能表和報告使用者功能表選取的按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCMenuButton : public CMFCButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|建構 `CMFCMenuButton` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|要轉譯的視窗訊息，再分派這些架構呼叫。 (覆寫 `CMFCButton::PreTranslateMessage`。)|  
|[CMFCMenuButton::SizeToContent](#sizetocontent)|根據其文字和影像的大小 按鈕的大小變更。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|指定是否要顯示預設的系統快顯功能表，或者使用[CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。|  
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|指定是否快顯功能表會出現下方或右邊的按鈕。|  
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|指定功能表按鈕是否要變更其狀態之後，使用者放開按鈕。|  
|[CMFCMenuButton::m_hMenu](#m_hmenu)|附加的 Windows 功能表的控制代碼。|  
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|識別項，表示哪些項目從快顯功能表選取的使用者。|  
  
## <a name="remarks"></a>備註  
 `CMFCMenuButton`類別衍生自[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)依次，衍生自[CButton 類別](../../mfc/reference/cbutton-class.md)。 因此，您可以使用`CMFCMenuButton`在您的程式碼會使用的相同方式`CButton`。  
  
 當您建立`CMFCMenuButton`，您必須傳遞給相關聯的快顯功能表中的控制代碼。 接下來，呼叫此函式`CMFCMenuButton::SizeToContent`。 `CMFCMenuButton::SizeToContent` 檢查足以包含指向快顯視窗出現的位置-也就是下或右邊的按鈕位置箭號按鈕的大小。  
  
## <a name="example"></a>範例  
 下列範例會示範如何設定附加至按鈕的功能表的控制代碼、 調整大小的按鈕，根據其文字和影像的大小，以及設定架構所顯示的快顯功能表。 此程式碼片段是部分[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxmenubutton.h  
  
##  <a name="cmfcmenubutton"></a>  CMFCMenuButton::CMFCMenuButton  
 建構新[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)物件。  
  
```  
CMFCMenuButton();
```  
  
##  <a name="m_bosmenu"></a>  CMFCMenuButton::m_bOSMenu  
 架構會顯示一個布林成員變數，指出哪一個快顯功能表。  
  
```  
BOOL m_bOSMenu;  
```  
  
### <a name="remarks"></a>備註  
 如果`m_bOSMenu`是`TRUE`，架構會呼叫繼承`TrackPopupMenu`此物件的方法。 否則，架構會呼叫[CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。  
  
##  <a name="m_brightarrow"></a>  CMFCMenuButton::m_bRightArrow  
 布林成員變數，指出快顯功能表的位置。  
  
```  
BOOL m_bRightArrow;  
```  
  
### <a name="remarks"></a>備註  
 當使用者按下功能表按鈕時，應用程式會顯示快顯功能表。 架構會顯示快顯功能表在按鈕下方或右邊的按鈕。 此按鈕還有一個小箭號，指出快顯功能表上出現的位置。 如果`m_bRightArrow`是`TRUE`，架構會顯示快顯功能表按鈕的右邊。 否則，它會顯示在按鈕下方的快顯功能表。  
  
##  <a name="m_bstaypressed"></a>  CMFCMenuButton::m_bStayPressed  
 雖然使用者會從快顯功能表選取項目，則按下布林成員變數，指出是否顯示功能表按鈕。  
  
```  
BOOL m_bStayPressed;  
```  
  
### <a name="remarks"></a>備註  
 如果`m_bStayPressed`成員是`FALSE`，功能表不會不會變成按下按鈕時使用者按下按鈕。 在此情況下，架構會顯示快顯的功能表。  
  
 如果`m_bStayPressed`成員是`TRUE`，當使用者按一下按鈕時，會變成已按下功能表按鈕。 它會直到已按下保持使用者關閉快顯功能表上，可以在選取範圍，或取消後。  
  
##  <a name="m_hmenu"></a>  CMFCMenuButton::m_hMenu  
 要附加的功能表的控制代碼。  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="remarks"></a>備註  
 架構會顯示由這個成員變數，當使用者按一下功能表按鈕的功能表。  
  
##  <a name="m_nmenuresult"></a>  CMFCMenuButton::m_nMenuResult  
 整數，表示哪些項目會從快顯功能表選取使用者。  
  
```  
int m_nMenuResult;  
```  
  
### <a name="remarks"></a>備註  
 這個成員變數的值為零，如果使用者取消功能表而不在選取範圍，或發生錯誤。  
  
##  <a name="pretranslatemessage"></a>  CMFCMenuButton::PreTranslateMessage  
 要轉譯的視窗訊息，再分派這些架構呼叫。  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pMsg`  
 指向[MSG](../../mfc/reference/msg-structure1.md)結構，其中包含要處理的訊息。  
  
### <a name="return-value"></a>傳回值  
 如果訊息已轉譯，而且不應該分派; 非零，如果訊息不翻譯，而且應該分派是 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="sizetocontent"></a>  CMFCMenuButton::SizeToContent  
 根據其文字大小和映像大小按鈕的大小變更。  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bCalcOnly`  
 布林值參數，指出是否此方法會調整大小的按鈕。  
  
### <a name="return-value"></a>傳回值  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，指定新按鈕的大小。  
  
### <a name="remarks"></a>備註  
 如果您呼叫此函式和`bCalcOnly`是`TRUE`，`SizeToContent`會計算按鈕的新大小。  
  
 新按鈕的大小計算為符合按鈕文字、 影像和箭號。 架構也會加入 10 個像素水平的邊緣和垂直邊緣 5 像素的預先定義的邊界。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)
