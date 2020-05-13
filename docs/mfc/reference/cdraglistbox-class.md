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
ms.openlocfilehash: 0d1ae94948e1143a5bac17985423c4bd1bfbaf65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374036"
---
# <a name="cdraglistbox-class"></a>CDragListBox 類別

除了提供 Windows 清單框的功能`CDragListBox`外, 該類別還允許使用者在清單框中行動清單框項(如檔名)。

## <a name="syntax"></a>語法

```
class CDragListBox : public CListBox
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDragListBox:CDraglistBox](#cdraglistbox)|建構 `CDragListBox` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDragListBox::開始拖動](#begindrag)|拖動操作開始時由框架調用。|
|[CDragListBox::取消拖動](#canceldrag)|當拖動操作被取消時由框架調用。|
|[CDragListBox::D](#dragging)|在拖動操作期間由框架調用。|
|[CDragListBox::D原始插入](#drawinsert)|繪製拖動清單框的插入指南。|
|[CDragListBox::D](#dropped)|刪除項後由框架調用。|
|[CDraglistBox::專案從Pt](#itemfrompt)|返回要拖動的項的座標。|

## <a name="remarks"></a>備註

具有此功能的清單框允許使用者以對它們最有用的任何方式對清單中的專案排序。 預設情況下,清單框會將專案移動到清單中的新位置。 但是,`CDragListBox`可以自定義物件以複製專案,而不是移動它們。

與`CDragListBox`類關聯的清單框控件不得具有LBS_SORT或LBS_MULTIPLESELECT樣式。 有關清單框樣式的說明,請參閱[清單框樣式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)。

要在應用程式的現有對話方塊中使用拖動清單框,請使用對話方塊編輯器向對話方塊樣本添加清單框控制項,然後分配與對話方塊樣本中的清單框控制項對應的成員變數(`Control`類別和變數類型)。 `CDragListBox`

有關將控制項分配給成員變數的詳細資訊,請參閱[為對話方塊定義成員變數的快捷方式](../../windows/defining-member-variables-for-dialog-controls.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="cdraglistboxbegindrag"></a><a name="begindrag"></a>CDragListBox::開始拖動

當可能發生可能開始拖動操作的事件(如按下滑鼠左鍵)時,由框架調用。

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
包含要拖動的項的座標的[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件。

### <a name="return-value"></a>傳回值

如果允許拖動,則不為零,否則為 0。

### <a name="remarks"></a>備註

如果要控制拖動操作開始時發生的情況,請覆蓋此函數。 默認實現捕獲滑鼠並保持拖動模式,直到用戶按一下滑鼠左鍵或右鍵或按 ESC,此時拖動操作將被取消。

## <a name="cdraglistboxcanceldrag"></a><a name="canceldrag"></a>CDragListBox::取消拖動

當拖動操作被取消時由框架調用。

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
包含要拖動的項的座標的[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件。

### <a name="remarks"></a>備註

重寫此函數以處理清單框控制項的任何特殊處理。

## <a name="cdraglistboxcdraglistbox"></a><a name="cdraglistbox"></a>CDragListBox:CDraglistBox

建構 `CDragListBox` 物件。

```
CDragListBox();
```

## <a name="cdraglistboxdragging"></a><a name="dragging"></a>CDragListBox::D

在`CDragListBox`物件內拖動清單框項時,由框架調用。

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
包含游標的 x 和 y 螢幕座標的[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件。

### <a name="return-value"></a>傳回值

要顯示的游標的資源 ID。 可以使用以下值:

- DL_COPYCURSOR指示將複製該專案。

- DL_MOVECURSOR指示將移動該專案。

- DL_STOPCURSOR指示當前放置目標不可接受。

### <a name="remarks"></a>備註

默認行為返回DL_MOVECURSOR。 如果要提供其他功能,請重寫此函數。

## <a name="cdraglistboxdrawinsert"></a><a name="drawinsert"></a>CDragListBox::D原始插入

由框架調用,以使用指示的索引在專案之前繪製插入指南。

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>參數

*nItem*<br/>
插入點的零索引。

### <a name="remarks"></a>備註

值 - 1 清除插入參考線。 重寫此函數以修改插入參考線的外觀或行為。

## <a name="cdraglistboxdropped"></a><a name="dropped"></a>CDragListBox::D

當項在`CDragListBox`物件中刪除時,由框架調用。

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>參數

*NSrcIndex*<br/>
指定刪除字串的零基索引。

*pt*<br/>
包含放置網站座標的[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件。

### <a name="remarks"></a>備註

預設行為將清單框項目及其資料複製到新位置,然後刪除原始項。 重寫此函數以自訂預設行為,例如啟用要拖動到清單中其他位置的清單框項的副本。

## <a name="cdraglistboxitemfrompt"></a><a name="itemfrompt"></a>CDraglistBox::專案從Pt

呼叫此函式以檢索位於*pt*的清單框項目的零基索引。

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>參數

*pt*<br/>
包含清單框中點座標的[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件。

*bAutoScroll*<br/>
如果允許滾動,則非零,否則為 0。

### <a name="return-value"></a>傳回值

拖動清單框項的零基索引。

## <a name="see-also"></a>另請參閱

[MFC 樣品 TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)
