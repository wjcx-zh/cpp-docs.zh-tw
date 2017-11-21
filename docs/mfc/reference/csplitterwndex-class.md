---
title: "CSplitterWndEx 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
dev_langs: C++
helpviewer_keywords: CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e45a136941ccaf34108085a14ddefb64bcdb3fa4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="csplitterwndex-class"></a>CSplitterWndEx 類別



表示自訂分割視窗。  
  
## <a name="syntax"></a>語法  
  
```  
class CSplitterWndEx : public CSplitterWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CSplitterWndEx::CSplitterWndEx`|預設建構函式。|  
|`CSplitterWndEx::~CSplitterWndEx`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|由架構呼叫以繪製分隔視窗。 (覆寫[CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter)。)|  
  
## <a name="remarks"></a>備註  
 覆寫`OnDrawSplitter`方法，以自訂的圖形化元件分隔視窗的外觀。  
  
 `CSplitterWndEx`類別會搭配[OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder)， [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)，和[OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground)方法，其為藉由視覺管理員。 若要使視覺管理員，以繪製您的應用程式中的分隔視窗，取代的宣告`CSplitterWnd`類別`CSplitterWndEx`類別。 框架視窗的應用程式，位於 mainfrm.h CMainFrame 類別中宣告的分隔視窗類別。 如需範例，請參閱`OutlookDemo`的 Samples 目錄中的範例。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 [CSplitterWnd](csplitterwnd-class.md)  
   
## <a name="requirements"></a>需求  
 **標頭：** afxsplitterwndex.h  
  
##  <a name="ondrawsplitter"></a>CSplitterWndEx::OnDrawSplitter  
 由架構呼叫以繪製分隔視窗。  
  
```  
virtual void OnDrawSplitter(  
   CDC* pDC,  
   ESplitType nType,  
   const CRect& rect   
);  
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。 如果這個參數是`NULL`，架構會重新繪製作用中視窗。  
  
 [in] `nType`  
 其中一個`CSplitterWnd::ESplitType`列舉值，指定要繪製的分隔視窗項目。 有效值為`splitBox`， `splitBar`， `splitIntersection`，和`splitBorder`。  
  
 [in] `rect`  
 指定的維度和位置繪製指定的分隔器視窗項目的周框。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../hierarchy-chart.md)   
 [類別](mfc-classes.md)   
 [CSplitterWnd 類別](csplitterwnd-class.md)   
 [CMFCVisualManager 類別](cmfcvisualmanager-class.md)