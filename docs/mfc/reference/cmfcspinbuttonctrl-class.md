---
title: "CMFCSpinButtonCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
dev_langs:
- C++
helpviewer_keywords:
- CMFCSpinButtonCtrl class
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: c1832062461f2ed53df07a72428089179ed493ab
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl 類別
`CMFCSpinButtonCtrl`類別支援繪製微調按鈕控制項的視覺管理員。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCSpinButtonCtrl : public CSpinButtonCtrl  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|預設建構函式。|  
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|會重新繪製目前的微調按鈕控制項。|  
  
## <a name="remarks"></a>備註  
 若要使用的視覺管理員，在您的應用程式中繪製微調按鈕控制項，來取代所有的執行個體的`CSpinButtonCtrl`類別`CMFCSpinButtonCtrl`類別。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立的物件`CMFCSpinButtonCtrl`類別，並且使用其`Create`方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&25;](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)  
  
 [CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxspinbuttonctrl.h  
  
##  <a name="ondraw"></a>CMFCSpinButtonCtrl::OnDraw  
 會重新繪製目前的微調按鈕控制項。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
### <a name="remarks"></a>備註  
 這個架構會呼叫`CMFCSpinButtonCtrl::OnPaint`方法以處理[CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint)訊息，以及該方法會呼叫這`CMFCSpinButtonCtrl::OnDraw`方法。 覆寫這個方法，以自訂架構繪製微調按鈕控制項的方式。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager 類別](../../mfc/reference/cmfcvisualmanager-class.md)

