---
title: "CMFCMenuButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCMenuButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCMenuButton class
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
caps.latest.revision: 32
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 65c334ce68dbbbae2b21da2c40aa9420cdeb51bd
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton 類別
顯示快顯功能表和報告使用者功能表選取的按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCMenuButton : public CMFCButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|建構 `CMFCMenuButton` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|要轉譯的視窗訊息，再分派這些架構呼叫。 (覆寫 `CMFCButton::PreTranslateMessage`。)|  
|[CMFCMenuButton::SizeToContent](#sizetocontent)|變更它的文字和影像的大小根據按鈕大小。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|指定是否要顯示的預設系統的快顯功能表，或是使用[CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。|  
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|指定是否快顯功能表會出現下方或右邊的按鈕。|  
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|指定是否功能表按鈕將其狀態變更之後，使用者放開按鈕。|  
|[CMFCMenuButton::m_hMenu](#m_hmenu)|附加的 Windows 功能表控制代碼。|  
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|識別項，表示哪些項目從快顯功能表上選取的使用者。|  
  
## <a name="remarks"></a>備註  
 `CMFCMenuButton`類別衍生自[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)反而，衍生自[CButton 類別](../../mfc/reference/cbutton-class.md)。 因此，您可以使用`CMFCMenuButton`在相同的方式，您可以使用程式碼中`CButton`。  
  
 當您建立`CMFCMenuButton`，您必須傳遞至相關聯的快顯功能表中的控制代碼。 接下來，呼叫函式`CMFCMenuButton::SizeToContent`。 `CMFCMenuButton::SizeToContent`檢查足以包含指向的位置快顯視窗中顯示的位置-也就是下面或按鈕右邊的箭號按鈕的大小。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定附加至按鈕的功能表的控制代碼、 縮放按鈕根據其文字和影像的大小，以及設定時所顯示的快顯功能表。 此程式碼片段是一部分[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&38;](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&39;](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxmenubutton.h  
  
##  <a name="a-namecmfcmenubuttona--cmfcmenubuttoncmfcmenubutton"></a><a name="cmfcmenubutton"></a>CMFCMenuButton::CMFCMenuButton  
 建構新[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)物件。  
  
```  
CMFCMenuButton();
```  
  
##  <a name="a-namembosmenua--cmfcmenubuttonmbosmenu"></a><a name="m_bosmenu"></a>CMFCMenuButton::m_bOSMenu  
 此布林值的成員變數會指出哪一個快顯功能表，架構會顯示。  
  
```  
BOOL m_bOSMenu;  
```  
  
### <a name="remarks"></a>備註  
 如果`m_bOSMenu`是`TRUE`，架構會呼叫繼承`TrackPopupMenu`此物件的方法。 否則，架構會呼叫[CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。  
  
##  <a name="a-namembrightarrowa--cmfcmenubuttonmbrightarrow"></a><a name="m_brightarrow"></a>CMFCMenuButton::m_bRightArrow  
 布林值的成員變數，指出快顯功能表上的位置。  
  
```  
BOOL m_bRightArrow;  
```  
  
### <a name="remarks"></a>備註  
 當使用者按下 [功能表] 按鈕時，應用程式會顯示快顯功能表。 架構會顯示快顯功能表 按鈕下方或右邊的按鈕。 此按鈕還有一個小箭號，指出快顯功能表上出現的位置。 如果`m_bRightArrow`是`TRUE`，架構會顯示快顯功能表按鈕的右邊。 否則，它會顯示快顯功能表 按鈕下方。  
  
##  <a name="a-namembstaypresseda--cmfcmenubuttonmbstaypressed"></a><a name="m_bstaypressed"></a>CMFCMenuButton::m_bStayPressed  
 雖然使用者可以從快顯功能表選取項目，按下的布林成員變數，指出是否顯示功能表 按鈕。  
  
```  
BOOL m_bStayPressed;  
```  
  
### <a name="remarks"></a>備註  
 如果`m_bStayPressed`成員是`FALSE`，功能表不會不會按下按鈕時，會使用按下按鈕。 在此情況下，架構會顯示快顯功能表。  
  
 如果`m_bStayPressed`成員是`TRUE`，當使用者按一下按鈕會變成已按下 [功能表] 按鈕。 使用者關閉快顯功能表上，藉由選取或取消之後，它會維持狀態直到按下。  
  
##  <a name="a-namemhmenua--cmfcmenubuttonmhmenu"></a><a name="m_hmenu"></a>CMFCMenuButton::m_hMenu  
 要附加的功能表的控制代碼。  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="remarks"></a>備註  
 架構會顯示由這個成員變數，當使用者按一下 [功能表] 按鈕的功能表。  
  
##  <a name="a-namemnmenuresulta--cmfcmenubuttonmnmenuresult"></a><a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult  
 整數，表示哪些項目會從快顯功能表上選取使用者。  
  
```  
int m_nMenuResult;  
```  
  
### <a name="remarks"></a>備註  
 這個成員變數的值為零，如果使用者取消功能表而不做選擇，或發生錯誤。  
  
##  <a name="a-namepretranslatemessagea--cmfcmenubuttonpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenuButton::PreTranslateMessage  
 要轉譯的視窗訊息，再分派這些架構呼叫。  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMsg`  
 指向[MSG](../../mfc/reference/msg-structure1.md)結構，其中包含要處理的訊息。  
  
### <a name="return-value"></a>傳回值  
 如果訊息已轉譯，而且不會發送，為非零如果訊息無法轉譯，而且應該分派到，0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesizetocontenta--cmfcmenubuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCMenuButton::SizeToContent  
 根據其文字大小和影像大小 按鈕的大小變更。  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bCalcOnly`  
 布林值的參數，指出是否此方法會調整大小 按鈕。  
  
### <a name="return-value"></a>傳回值  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，指定新按鈕的大小。  
  
### <a name="remarks"></a>備註  
 如果您呼叫此函式和`bCalcOnly`是`TRUE`，`SizeToContent`會先計算按鈕的新大小。  
  
 新按鈕的大小計算為符合按鈕文字、 影像和箭號。 架構也會加入 10 個像素水平的邊緣和 5 個像素垂直邊緣的預先定義的邊界。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)

