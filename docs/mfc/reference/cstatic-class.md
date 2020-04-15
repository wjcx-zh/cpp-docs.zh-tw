---
title: CStatic 類別
ms.date: 11/04/2016
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
ms.openlocfilehash: e5c3705c0aa2fd90e73cb54ba5a97c252ed2cf83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371648"
---
# <a name="cstatic-class"></a>CStatic 類別

提供 Windows 靜態控制項的功能。

## <a name="syntax"></a>語法

```
class CStatic : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[靜態::靜態](#cstatic)|建構 `CStatic` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[靜態::創建](#create)|創建 Windows 靜態控制件並將其`CStatic`附加到 物件。|
|[靜態::D原始專案](#drawitem)|覆蓋以繪製所有者繪製的靜態控件。|
|[靜態::獲取位圖](#getbitmap)|檢索以前使用[SetBitmap](#setbitmap)設置的位圖的句柄。|
|[靜態::獲取游標](#getcursor)|檢索以前使用[SetCursor](#setcursor)設定的游標影像的句柄。|
|[靜態::取得EnhMetaFile](#getenhmetafile)|檢索以前使用[SetEnhMetaFile](#setenhmetafile)設定的擴增中檔案的句柄。|
|[靜態::獲取圖示](#geticon)|檢索以前使用[SetIcon](#seticon)設定的圖示的句柄。|
|[靜態::設置位圖](#setbitmap)|指定要在靜態控制項中顯示的點陣圖。|
|[靜態::設置游標](#setcursor)|指定要在靜態控制項中顯示的游標影像。|
|[靜態::SetEnhMetaFile](#setenhmetafile)|指定要在靜態控制項中顯示的增強元檔。|
|[靜態::設定圖示](#seticon)|指定要在靜態控制項中顯示的圖示。|

## <a name="remarks"></a>備註

靜態控制項顯示文字字串、框、矩形、圖示、游標、點陣圖或增強的元檔。 它可用於標記、框或分隔其他控制項。 靜態控件通常不需要輸入,並且不提供輸出;但是,如果滑鼠按兩下是使用SS_NOTIFY樣式創建的,則可以通知其父級滑鼠按一下。

分兩步創建靜態控件。 首先,調用構造函數構造`CStatic`物件,然後調用[Create](#create)成員函數以創建靜態控制件並將`CStatic`其附加到 物件。

如果在對話框中創建`CStatic`物件(通過對話框資源),則當使用者關閉對話方塊`CStatic`時, 該物件將自動銷毀。

如果在視窗中創建`CStatic`物件,則可能需要銷毀它。 在`CStatic`視窗內的堆疊上創建的物件將自動銷毀。 如果使用**新**函數在`CStatic`堆上創建物件,**則必須調用**delete 物件以在使用該物件時銷毀該物件。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cstaticcreate"></a><a name="create"></a>靜態::創建

創建 Windows 靜態控制件並將其`CStatic`附加到 物件。

```
virtual BOOL Create(
    LPCTSTR lpszText,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID = 0xffff);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
指定要放置在控制器中的文字。 如果為 NULL,則看不到任何文字。

*dwStyle*<br/>
指定靜態控制件的視窗樣式。 將[靜態控件樣式](../../mfc/reference/styles-used-by-mfc.md#static-styles)的任意組合應用於控制項。

*矩形*<br/>
指定靜態控制者的位置和大小。 它可以是`RECT`結構或`CRect`物件。

*pparentwnd*<br/>
指定`CStatic`父視窗,通常是`CDialog`物件。 它不得為 NULL。

*nID*<br/>
指定靜態控制件的控制 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

分兩`CStatic`步構造物件。 首先調用構造函數`CStatic`,然後調`Create`用 ,這將創建 Windows 靜態控件`CStatic`並將其附加到 物件。

將以下[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)套用於靜態控制者:

- WS_CHILD始終

- WS_VISIBLE 通常

- WS_DISABLED很少

如果要在靜態控制項中顯示點陣圖、游標、圖示或元檔,則需要應用以下[靜態樣式](../../mfc/reference/styles-used-by-mfc.md#static-styles)之一:

- SS_BITMAP 此樣式用於位圖。

- SS_ICON 此樣式用於光標和圖示。

- SS_ENHMETAFILE使用此樣式增強元檔。

對於游標、點陣圖或圖示,您可能還需要使用以下樣式:

- SS_CENTERIMAGE 用於將圖像居中居於靜態控件中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

## <a name="cstaticcstatic"></a><a name="cstatic"></a>靜態::靜態

建構 `CStatic` 物件。

```
CStatic();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

## <a name="cstaticdrawitem"></a><a name="drawitem"></a>靜態::D原始專案

由框架調用以繪製所有者繪製的靜態控制件。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDraw 專案已結*<br/>
指向[DRAWITEMSTRUCT 結構的](/windows/win32/api/winuser/ns-winuser-drawitemstruct)指標。 結構包含有關要繪製的項和所需繪圖類型的資訊。

### <a name="remarks"></a>備註

重寫此函數以實現擁有者繪製`CStatic`的對象的繪圖(控制件具有樣式SS_OWNERDRAW)。

## <a name="cstaticgetbitmap"></a><a name="getbitmap"></a>靜態::獲取位圖

獲取點陣圖的句柄,以前使用[SetBitmap](#setbitmap)設置,該`CStatic`句柄與相關聯。

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>傳回值

當前位圖的句柄,如果未設置位圖,則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticgetcursor"></a><a name="getcursor"></a>靜態::獲取游標

獲取以前使用[SetCursor](#setcursor)設定`CStatic`的與 關聯的游標的句柄。

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>傳回值

目前游標的句柄,如果未設置游標,則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticgetenhmetafile"></a><a name="getenhmetafile"></a>靜態::取得EnhMetaFile

獲取增強型元檔的句柄,以前使用[SetEnhMetafile](#setenhmetafile)設置,該`CStatic`文件與 相關聯。

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>傳回值

當前增強的元檔句柄,如果未設置增強的元檔,則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticgeticon"></a><a name="geticon"></a>靜態::獲取圖示

獲取以前使用[SetIcon](#seticon)設置的圖示的句柄,該句`CStatic`柄與 相關聯。

```
HICON GetIcon() const;
```

### <a name="return-value"></a>傳回值

目前圖示的句柄,如果未設置圖示,則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="cstaticsetbitmap"></a><a name="setbitmap"></a>靜態::設置位圖

將新的位圖與靜態控件關聯。

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
要在靜態控件中繪製的點陣圖的句柄。

### <a name="return-value"></a>傳回值

以前與靜態控件關聯的位圖的句柄,如果沒有位圖與靜態控件關聯的則 NULL 的句柄。

### <a name="remarks"></a>備註

位圖將自動在靜態控制件中繪製。 默認情況下,它將在左上角繪製,靜態控件將調整為位圖的大小。

您可以使用各種視窗和靜態控制樣式,包括:

- SS_BITMAP 始終使用此樣式進行位圖。

- SS_CENTERIMAGE 用於將圖像居中居於靜態控件中。 如果圖像大於靜態控件,則將剪切它。 如果小於靜態控件,則圖像周圍的空白空間將由位圖左上角的像素顏色填充。

- MFC 提供`CBitmap`類 ,當您必須對位圖圖像執行更多操作時,可以使用該類,而不僅僅是調用`LoadBitmap`Win32 函數。 `CBitmap`包含一種 GDI 物件,`CStatic`通常與配合使用`CWnd`,該 物件用於將圖形對象顯示為靜態控制件。

`CImage`是 ATL/MFC 類,可讓您更輕鬆地使用設備獨立位圖 (DIB)。 有關詳細資訊,請參閱[CImage 類別](../../atl-mfc-shared/reference/cimage-class.md)。

- 典型用法是提供`CStatic::SetBitmap``CBitmap`由`CImage`或物件的 HBITMAP 運算符返回的 GDI 物件。 執行此操作的代碼類似於以下行。

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```

下面的範例在堆上`CStatic`創建兩個物件。 然後,它使用`CBitmap::LoadOEMBitmap`系統位圖載入一個,從使用`CImage::Load`的檔載入另一個。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticsetcursor"></a><a name="setcursor"></a>靜態::設置游標

將新的游標圖像與靜態控件關聯。

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>參數

*h游標*<br/>
要在靜態控件中繪製的游標的句柄。

### <a name="return-value"></a>傳回值

以前與靜態控件關聯的游標的句柄,如果沒有與靜態控件關聯的游標,則為 NULL。

### <a name="remarks"></a>備註

游標將自動在靜態控制件中繪製。 默認情況下,它將在左上角繪製,靜態控件將調整為游標的大小。

您可以使用各種視窗和靜態控制樣式,包括:

- SS_ICON 始終使用此樣式用於游標和圖示。

- SS_CENTERIMAGE 用於在靜態控件中居中。 如果圖像大於靜態控件,則將剪切它。 如果小於靜態控件,則圖像周圍的空白空間將填充靜態控件的背景顏色。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticsetenhmetafile"></a><a name="setenhmetafile"></a>靜態::SetEnhMetaFile

將新的增強元檔映射與靜態控件關聯。

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>參數

*hMetaFile*<br/>
要在靜態控件中繪製的增強元檔的句柄。

### <a name="return-value"></a>傳回值

以前與靜態控件關聯的增強元檔的句柄,如果沒有與靜態控件關聯的增強元檔,則 NULL 的句柄。

### <a name="remarks"></a>備註

增強的元檔將自動在靜態控件中繪製。 增強的元檔將縮放以適合靜態控件的大小。

您可以使用各種視窗和靜態控制樣式,包括:

- SS_ENHMETAFILE 始終使用此樣式進行增強的元檔。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticseticon"></a><a name="seticon"></a>靜態::設定圖示

將新的圖示圖像與靜態控件關聯。

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>參數

*hIcon*<br/>
要在靜態控件中繪製的圖示的句柄。

### <a name="return-value"></a>傳回值

以前與靜態控件關聯的圖示的句柄,如果沒有與靜態控件關聯的圖示,則為 NULL。

### <a name="remarks"></a>備註

圖示將自動在靜態控制件中繪製。 默認情況下,它將在左上角繪製,靜態控件將調整為圖示的大小。

您可以使用各種視窗和靜態控制樣式,包括:

- SS_ICON 始終使用此樣式用於游標和圖示。

- SS_CENTERIMAGE 用於在靜態控件中居中。 如果圖像大於靜態控件,則將剪切它。 如果小於靜態控件,則圖像周圍的空白空間將填充靜態控件的背景顏色。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
