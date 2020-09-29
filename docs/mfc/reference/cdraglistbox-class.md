---
title: CDragListBox 類別
ms.date: 11/04/2016
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
ms.openlocfilehash: b260d3a88fc8c3f2d341005c1e47cfd9ab668e1e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500361"
---
# <a name="cdraglistbox-class"></a>CDragListBox 類別

除了提供 Windows 清單方塊的功能之外，此類別還可 `CDragListBox` 讓使用者在清單方塊內移動清單方塊專案，例如檔案名。

## <a name="syntax"></a>語法

```
class CDragListBox : public CListBox
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDragListBox：： CDragListBox](#cdraglistbox)|建構 `CDragListBox` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDragListBox：： BeginDrag](#begindrag)|當拖曳作業開始時由架構呼叫。|
|[CDragListBox：： CancelDrag](#canceldrag)|當拖曳作業取消時，由架構呼叫。|
|[CDragListBox：:D ragging](#dragging)|在拖曳作業期間由架構呼叫。|
|[CDragListBox：:D rawInsert](#drawinsert)|繪製拖曳清單方塊的插入指南。|
|[CDragListBox：:D ropped](#dropped)|在刪除專案之後，由架構呼叫。|
|[CDragListBox：： ItemFromPt](#itemfrompt)|傳回所拖曳專案的座標。|

## <a name="remarks"></a>備註

具有這項功能的清單方塊可讓使用者以最有用的方式來排序清單中的專案。 根據預設，清單方塊會將專案移到清單中的新位置。 不過，您 `CDragListBox` 可以自訂物件來複製專案，而不是移動專案。

與類別相關聯的清單方塊控制項 `CDragListBox` 不能有 LBS_SORT 或 LBS_MULTIPLESELECT 的樣式。 如需清單方塊樣式的描述，請參閱 [清單方塊樣式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)。

若要在應用程式的現有對話方塊中使用拖曳清單方塊，請使用對話方塊編輯器將清單方塊控制項新增至對話方塊範本，然後將類別和變數類型 (的成員變數 `Control` `CDragListBox`) 對應至對話方塊範本中的清單方塊控制項。

如需將控制項指派給成員變數的詳細資訊，請參閱 [為對話方塊控制項定義成員變數的快捷方式](../../windows/adding-editing-or-deleting-controls.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="cdraglistboxbegindrag"></a><a name="begindrag"></a> CDragListBox：： BeginDrag

當事件發生時，由架構呼叫，這可能會開始拖曳作業，例如按下滑鼠左鍵。

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含所拖曳專案的座標。

### <a name="return-value"></a>傳回值

如果允許拖曳則為非零，否則為0。

### <a name="remarks"></a>備註

如果您想要控制在拖曳作業開始時所發生的情況，請覆寫這個函式。 預設的執行會捕捉滑鼠並保持在拖曳模式，直到使用者按下滑鼠左鍵或右鍵，或是按下 ESC 鍵，此時拖曳作業才會取消。

## <a name="cdraglistboxcanceldrag"></a><a name="canceldrag"></a> CDragListBox：： CancelDrag

當拖曳作業取消時，由架構呼叫。

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含所拖曳專案的座標。

### <a name="remarks"></a>備註

覆寫此函式可處理您清單方塊控制項的任何特殊處理。

## <a name="cdraglistboxcdraglistbox"></a><a name="cdraglistbox"></a> CDragListBox：： CDragListBox

建構 `CDragListBox` 物件。

```
CDragListBox();
```

## <a name="cdraglistboxdragging"></a><a name="dragging"></a> CDragListBox：:D ragging

當清單方塊專案正在拖曳至物件內時由架構呼叫 `CDragListBox` 。

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含游標的 x 和 y 螢幕座標。

### <a name="return-value"></a>傳回值

要顯示之資料指標的資源識別碼。 可能的值如下：

- DL_COPYCURSOR 指出將複製專案。

- DL_MOVECURSOR 指出將移動專案。

- DL_STOPCURSOR 表示無法接受目前的放置目標。

### <a name="remarks"></a>備註

預設行為會傳回 DL_MOVECURSOR。 如果您想要提供額外的功能，請覆寫此函數。

## <a name="cdraglistboxdrawinsert"></a><a name="drawinsert"></a> CDragListBox：:D rawInsert

由架構呼叫，以在具有指定索引的專案之前繪製插入指南。

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>參數

*nItem*<br/>
以零為基底的插入點索引。

### <a name="remarks"></a>備註

-1 的值會清除插入指南。 覆寫此函數以修改插入指南的外觀或行為。

## <a name="cdraglistboxdropped"></a><a name="dropped"></a> CDragListBox：:D ropped

當專案在物件內卸載時，由架構呼叫 `CDragListBox` 。

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>參數

*nSrcIndex*<br/>
指定已卸載字串以零為起始的索引。

*pt*<br/>
[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含放置位置的座標。

### <a name="remarks"></a>備註

預設行為會將清單方塊專案和它的資料複製到新的位置，然後刪除原始專案。 覆寫這個函式以自訂預設行為，例如啟用清單方塊專案的複本，以拖曳至清單中的其他位置。

## <a name="cdraglistboxitemfrompt"></a><a name="itemfrompt"></a> CDragListBox：： ItemFromPt

呼叫此函式可取得以零為起始的清單方塊專案索引（以 *pt*為依據）。

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>參數

*pt*<br/>
[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含清單方塊中某個點的座標。

*bAutoScroll*<br/>
如果允許滾動則為非零，否則為0。

### <a name="return-value"></a>傳回值

以零為基底的拖曳清單方塊專案索引。

## <a name="see-also"></a>另請參閱

[MFC 範例 TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)
