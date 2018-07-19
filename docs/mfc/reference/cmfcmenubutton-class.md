---
title: CMFCMenuButton 類別 |Microsoft Docs
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
ms.openlocfilehash: 77762fe12ed74f11f0b7e633f2a0c77523a7efaa
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849785"
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
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|由架構呼叫以轉譯視窗訊息，再將它們分派。 (覆寫 `CMFCButton::PreTranslateMessage`。)|  
|[CMFCMenuButton::SizeToContent](#sizetocontent)|變更其文字和影像的大小根據按鈕大小。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|指定是否要顯示的預設系統的快顯功能表，或使用[CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。|  
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|指定是否快顯功能表會出現下方或右邊的按鈕。|  
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|指定之後，使用者放開按鈕的功能表按鈕是否變更其狀態。|  
|[CMFCMenuButton::m_hMenu](#m_hmenu)|附加的 Windows 功能表控制代碼。|  
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|識別項，表示哪一個項目從快顯功能表中選取使用者。|  
  
## <a name="remarks"></a>備註  
 `CMFCMenuButton`類別衍生自[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)反而，衍生自[CButton 類別](../../mfc/reference/cbutton-class.md)。 因此，您可以使用`CMFCMenuButton`在您的程式碼會使用的相同方式`CButton`。  
  
 當您建立`CMFCMenuButton`，您必須傳遞控制代碼相關聯的快顯功能表。 接下來，呼叫此函式`CMFCMenuButton::SizeToContent`。 `CMFCMenuButton::SizeToContent` 檢查足以包含指向的位置的快顯視窗中出現的位置-也就是下或右邊的按鈕箭號按鈕的大小。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定附加至按鈕的功能表的控制代碼、 調整大小的按鈕，根據其文字和影像的大小，以及設定此架構會顯示快顯功能表。 此程式碼片段是一部分[新的控制項範例](../../visual-cpp-samples.md)。  
  
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
 一個布林成員變數，指出哪一個快顯功能表，架構會顯示。  
  
```  
BOOL m_bOSMenu;  
```  
  
### <a name="remarks"></a>備註  
 如果`m_bOSMenu`為 TRUE 時，架構會呼叫繼承`TrackPopupMenu`此物件的方法。 否則，架構會呼叫[CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。  
  
##  <a name="m_brightarrow"></a>  CMFCMenuButton::m_bRightArrow  
 布林值的成員變數，指出快顯功能表的位置。  
  
```  
BOOL m_bRightArrow;  
```  
  
### <a name="remarks"></a>備註  
 當使用者按下功能表按鈕時，應用程式會顯示快顯功能表。 此架構會顯示快顯功能表程式 按鈕或使用右邊的按鈕。 此按鈕還有一個小箭號，指出快顯功能表會出現的位置。 如果`m_bRightArrow`為 TRUE 時，架構會顯示快顯功能表按鈕的右邊。 否則，它會顯示快顯功能表 按鈕下方。  
  
##  <a name="m_bstaypressed"></a>  CMFCMenuButton::m_bStayPressed  
 布林值的成員變數，指出是否要顯示的功能表按鈕按下時使用者會從快顯功能表選取項目。  
  
```  
BOOL m_bStayPressed;  
```  
  
### <a name="remarks"></a>備註  
 如果`m_bStayPressed`成員設為 FALSE，功能表不會不會按下按鈕時使用者按下按鈕。 在此情況下，架構會顯示快顯功能表。  
  
 如果`m_bStayPressed`成員為 TRUE，當使用者按一下按鈕時，會變成已按下功能表按鈕。 它之後會保持已按下，直到使用者關閉快顯功能表上，藉由確定選取範圍，或取消。  
  
##  <a name="m_hmenu"></a>  CMFCMenuButton::m_hMenu  
 要附加的功能表的控制代碼。  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="remarks"></a>備註  
 架構會顯示使用者按下功能表按鈕時，此成員變數所指定的功能表。  
  
##  <a name="m_nmenuresult"></a>  CMFCMenuButton::m_nMenuResult  
 整數，指出哪一個項目從快顯功能表中選取使用者。  
  
```  
int m_nMenuResult;  
```  
  
### <a name="remarks"></a>備註  
 此成員變數的值為零，如果使用者取消 [] 功能表，而不進行選取，或發生錯誤。  
  
##  <a name="pretranslatemessage"></a>  CMFCMenuButton::PreTranslateMessage  
 由架構呼叫以轉譯視窗訊息，再將它們分派。  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>參數  
 [in]*pMsg*  
 指向[MSG](../../mfc/reference/msg-structure1.md)結構，其中包含要處理的訊息。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果訊息已轉譯，而且不應該分派;如果訊息未被翻譯，因此應該分派，0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="sizetocontent"></a>  CMFCMenuButton::SizeToContent  
 根據其文字大小和映像大小按鈕的大小變更。  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in]*bCalcOnly*  
 布林值參數，指出是否此方法會調整大小的按鈕。  
  
### <a name="return-value"></a>傳回值  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，指定按鈕的新大小。  
  
### <a name="remarks"></a>備註  
 如果您呼叫此函式和*bCalcOnly*為 TRUE，`SizeToContent`會計算按鈕的新大小。  
  
 新按鈕的大小會計算成按鈕文字、 影像和箭號。 此架構也會加入預先定義的 10 個像素水平的邊緣和垂直邊緣的 5 個像素的邊界。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)
