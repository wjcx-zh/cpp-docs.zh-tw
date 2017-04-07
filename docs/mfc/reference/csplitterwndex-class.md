---
title: "CSplitterWndEx 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
dev_langs:
- C++
helpviewer_keywords:
- CSplitterWndEx
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
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
ms.sourcegitcommit: 73410ae17465880f455e5b15026f6cc010803c19
ms.openlocfilehash: 08b26bc2321485181941dbaaa9a903de9a401ef8
ms.lasthandoff: 02/24/2017

---
# <a name="csplitterwndex-class"></a>CSplitterWndEx 類別



表示自訂分割視窗。  
  
## <a name="syntax"></a>語法  
  
```  
class CSplitterWndEx : public CSplitterWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CSplitterWndEx::CSplitterWndEx`|預設建構函式。|  
|`CSplitterWndEx::~CSplitterWndEx`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|若要繪製的分隔視窗架構呼叫。 (覆寫[CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter)。)|  
  
## <a name="remarks"></a>備註  
 覆寫`OnDrawSplitter`方法，以自訂分割視窗中的圖形化元件的外觀。  
  
 `CSplitterWndEx`類別會搭配[OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder)， [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)，和[OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground)的視覺管理員所實作的方法。 若要使繪製您的應用程式中的分隔視窗的視覺管理員，來取代的宣告`CSplitterWnd`類別`CSplitterWndEx`類別。 框架視窗應用程式，位於 mainfrm.h CMainFrame 類別中宣告的分隔視窗類別。 如需範例，請參閱`OutlookDemo`範例目錄中的範例。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 [CSplitterWnd](csplitterwnd-class.md)  
   
## <a name="requirements"></a>需求  
 **標頭︰** afxsplitterwndex.h  
  
##  <a name="ondrawsplitter"></a>CSplitterWndEx::OnDrawSplitter  
 若要繪製的分隔視窗架構呼叫。  
  
```  
virtual void OnDrawSplitter(  
   CDC* pDC,  
   ESplitType nType,  
   const CRect& rect   
);  
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容指標。 如果這個參數是`NULL`，架構會重新繪製的使用中視窗。  
  
 [in] `nType`  
 其中一個`CSplitterWnd::ESplitType`列舉值，指定要繪製的分隔視窗項目。 有效值為`splitBox`， `splitBar`， `splitIntersection`，和`splitBorder`。  
  
 [in] `rect`  
 指定位置繪製指定的分隔器視窗項目和維度的週框。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../hierarchy-chart.md)   
 [類別](mfc-classes.md)   
 [CSplitterWnd 類別](csplitterwnd-class.md)   
 [CMFCVisualManager 類別](cmfcvisualmanager-class.md)
