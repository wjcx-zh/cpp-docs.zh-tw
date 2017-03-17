---
title: "CListView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CListView
- AFXCVIEW/CListView
- AFXCVIEW/CListView::CListView
- AFXCVIEW/CListView::GetListCtrl
- AFXCVIEW/CListView::RemoveImageList
dev_langs:
- C++
helpviewer_keywords:
- views, and common controls
- CListView class
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
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
ms.openlocfilehash: ebf6c93aa6d88d1942af4ecb9e3373fa57d84b65
ms.lasthandoff: 02/24/2017

---
# <a name="clistview-class"></a>CListView 類別
簡化了使用清單控制項及[CListCtrl](../../mfc/reference/clistctrl-class.md)，封裝清單控制項功能，透過 MFC 的文件檢視架構的類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CListView : public CCtrlView  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CListView::CListView](#clistview)|建構 `CListView` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CListView::GetListCtrl](#getlistctrl)|傳回與檢視相關聯的清單控制項。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CListView::RemoveImageList](#removeimagelist)|從清單檢視中移除指定的映像的清單。|  
  
## <a name="remarks"></a>備註  
 如需有關這個架構的詳細資訊，請參閱概觀[CView](../../mfc/reference/cview-class.md)類別，而且那里引用的交互參考。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CListView`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxcview.h  
  
##  <a name="clistview"></a>CListView::CListView  
 建構 `CListView` 物件。  
  
```  
CListView();
```  
  
##  <a name="getlistctrl"></a>CListView::GetListCtrl  
 呼叫此成員函式可取得與檢視相關聯的清單控制項的參考。  
  
```  
CListCtrl& GetListCtrl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 檢視相關聯的清單控制項的參考。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCListView #&7;](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]  
  
##  <a name="removeimagelist"></a>CListView::RemoveImageList  
 從清單檢視中移除指定的映像的清單。  
  
```  
void RemoveImageList(int nImageList);
```  
  
### <a name="parameters"></a>參數  
 `nImageList`  
 若要移除映像的以零起始的索引。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 ROWLIST](../../visual-cpp-samples.md)   
 [CCtrlView 類別](../../mfc/reference/cctrlview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCtrlView 類別](../../mfc/reference/cctrlview-class.md)

