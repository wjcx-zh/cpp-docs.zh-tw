---
title: CListView 類別
ms.date: 11/04/2016
f1_keywords:
- CListView
- AFXCVIEW/CListView
- AFXCVIEW/CListView::CListView
- AFXCVIEW/CListView::GetListCtrl
- AFXCVIEW/CListView::RemoveImageList
helpviewer_keywords:
- CListView [MFC], CListView
- CListView [MFC], GetListCtrl
- CListView [MFC], RemoveImageList
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
ms.openlocfilehash: ae1a76e4cdd052ff44dcbd69d467c51741bcc2ff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370143"
---
# <a name="clistview-class"></a>CListView 類別

使用 MFC 的文件檢視架構結構簡化了清單控制件和[CListCtrl(](../../mfc/reference/clistctrl-class.md)封裝清單控制功能的類)的使用。

## <a name="syntax"></a>語法

```
class CListView : public CCtrlView
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CListView:CListView](#clistview)|建構 `CListView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CListView:取得清單Ctrl](#getlistctrl)|返回與檢視關聯的清單控制件。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CList查看:刪除圖片清單](#removeimagelist)|從清單檢視中刪除指定的影像清單。|

## <a name="remarks"></a>備註

有關此體系結構的詳細資訊,請參閱[CView](../../mfc/reference/cview-class.md)類的概述以及其中引用的交叉引用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>需求

**標題:** afxcview.h

## <a name="clistviewclistview"></a><a name="clistview"></a>CListView:CListView

建構 `CListView` 物件。

```
CListView();
```

## <a name="clistviewgetlistctrl"></a><a name="getlistctrl"></a>CListView:取得清單Ctrl

呼叫此成員函數以獲取對與檢視關聯的清單控制件的引用。

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>傳回值

對與檢視關聯的清單控制件的引用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

## <a name="clistviewremoveimagelist"></a><a name="removeimagelist"></a>CList查看:刪除圖片清單

從清單檢視中刪除指定的影像清單。

```
void RemoveImageList(int nImageList);
```

### <a name="parameters"></a>參數

*n 影像清單*<br/>
要刪除的圖像的零基索引。

## <a name="see-also"></a>另請參閱

[MFC 樣品 ROWLIST](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)
