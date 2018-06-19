---
title: CListView 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CListView [MFC], CListView
- CListView [MFC], GetListCtrl
- CListView [MFC], RemoveImageList
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3930ad915ff908b8931733a9f0362320e24dc2cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366339"
---
# <a name="clistview-class"></a>CListView 類別
可簡化使用清單控制項和[CListCtrl](../../mfc/reference/clistctrl-class.md)，封裝清單控制項功能，透過 MFC 的文件檢視架構的類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CListView : public CCtrlView  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CListView::CListView](#clistview)|建構 `CListView` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CListView::GetListCtrl](#getlistctrl)|傳回與檢視相關聯的清單控制項。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CListView::RemoveImageList](#removeimagelist)|從清單檢視中移除指定的映像清單。|  
  
## <a name="remarks"></a>備註  
 如需有關這個架構的詳細資訊，請參閱概觀[CView](../../mfc/reference/cview-class.md)類別，並那里所提到的交互參考。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CListView`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcview.h  
  
##  <a name="clistview"></a>  CListView::CListView  
 建構 `CListView` 物件。  
  
```  
CListView();
```  
  
##  <a name="getlistctrl"></a>  CListView::GetListCtrl  
 呼叫此成員函式可取得清單控制項與檢視相關聯的參考。  
  
```  
CListCtrl& GetListCtrl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 與檢視相關聯清單控制項的參考。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]  
  
##  <a name="removeimagelist"></a>  CListView::RemoveImageList  
 從清單檢視中移除指定的映像清單。  
  
```  
void RemoveImageList(int nImageList);
```  
  
### <a name="parameters"></a>參數  
 `nImageList`  
 映像以移除以零為起始的索引。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 ROWLIST](../../visual-cpp-samples.md)   
 [CCtrlView 類別](../../mfc/reference/cctrlview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCtrlView 類別](../../mfc/reference/cctrlview-class.md)
