---
title: "CMFCPropertyGridToolTipCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl class
- CMFCPropertyGridToolTipCtrl class, destructor
- PreTranslateMessage method
- ~CMFCPropertyGridToolTipCtrl destructor
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
caps.latest.revision: 24
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
ms.openlocfilehash: e5290706799dcd253205ac74dad72cd7783d19dd
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl 類別
實作的工具提示控制項[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)用來顯示工具提示。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCPropertyGridToolTipCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|說明|  
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|建構 `CMFCPropertyGridToolTipCtrl` 物件。|  
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|說明|  
|[CMFCPropertyGridToolTipCtrl::Create](#create)|建立工具提示控制項的視窗。|  
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|停用並隱藏工具提示控制項。|  
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|傳回工具提示控制項的最後一個位置的座標。|  
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|隱藏工具提示控制項。|  
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|類別所使用的[CWinApp](../../mfc/reference/cwinapp-class.md)轉譯視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 (覆寫[CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|設定工具提示文字與工具提示視窗的框線之間的間距。|  
|[CMFCPropertyGridToolTipCtrl::Track](#track)|顯示工具提示控制項。|  
  
## <a name="remarks"></a>備註  
 當指標停留在屬性名稱，會顯示工具提示。 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)類別會顯示工具提示，讓使用者容易閱讀。 工具提示的位置通常取決於指標的位置。 藉由使用這個類別，工具提示會出現在屬性名稱和自然屬性擴充中，類似於以屬性名稱是完全可見的。  
  
 MFC 會自動建立這個控制項及使用它在[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCPropertyGridToolTipCtrl`類別，以及如何顯示工具提示控制項。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&23;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxpropertygridtooltipctrl.h  
  
##  <a name="cmfcpropertygridtooltipctrl"></a>CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl  
 建構 `CMFCPropertyGridToolTipCtrl` 物件。  
  
```  
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```  
  
##  <a name="create"></a>CMFCPropertyGridToolTipCtrl::Create  
 建立工具提示控制項的視窗。  
  
```  
BOOL Create(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndParent`  
 父視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 已成功建立視窗; 如果為 TRUE否則為 FALSE。  
  
##  <a name="deactivate"></a>CMFCPropertyGridToolTipCtrl::Deactivate  
 停用並隱藏工具提示控制項。  
  
```  
void Deactivate();
```  
  
### <a name="remarks"></a>備註  
 這個方法會設定的最後一個位置和文字為空值，以便未來呼叫[CMFCPropertyGridToolTipCtrl::Track](#track)顯示工具提示。  
  
##  <a name="getlastrect"></a>CMFCPropertyGridToolTipCtrl::GetLastRect  
 傳回工具提示控制項的最後一個位置的座標。  
  
```  
void GetLastRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rect`  
 包含工具提示控制項的最後一個位置。  
  
##  <a name="hide"></a>CMFCPropertyGridToolTipCtrl::Hide  
 隱藏工具提示控制項。  
  
```  
void Hide();
```  
  
##  <a name="settextmargin"></a>CMFCPropertyGridToolTipCtrl::SetTextMargin  
 設定工具提示文字與工具提示視窗的框線之間的間距。  
  
```  
void SetTextMargin(int nTextMargin);
```  
  
### <a name="parameters"></a>參數  
 [in] `nTextMargin`  
 指定工具提示控制項的文字和工具提示視窗的框線之間的間距。 預設值為 10 個像素。  
  
##  <a name="track"></a>CMFCPropertyGridToolTipCtrl::Track  
 顯示工具提示控制項。  
  
```  
void Track(
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>參數  
 [in] `rect`  
 指定的位置和工具提示控制項的大小。  
  
 [in] `strText`  
 指定要顯示在工具提示文字。  
  
### <a name="remarks"></a>備註  
 這個方法會顯示工具提示控制項的位置與指定的大小`rect`。 如果自從上次呼叫這個方法未變更的位置、 大小和文字，則這個方法沒有任何作用。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

