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
ms.openlocfilehash: fd7b6787b372e220a32770e19d54d149f5ba6934
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502408"
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
|[CStatic::CStatic](#cstatic)|建構 `CStatic` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStatic::Create](#create)|建立 Windows 靜態控制項, 並將它附加至`CStatic`物件。|
|[CStatic::DrawItem](#drawitem)|覆寫以繪製主控描繪的靜態控制項。|
|[CStatic::GetBitmap](#getbitmap)|抓取先前使用[SetBitmap](#setbitmap)設定之點陣圖的控制碼。|
|[CStatic::GetCursor](#getcursor)|抓取先前使用[SetCursor](#setcursor)設定之資料指標影像的控制碼。|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|抓取先前使用[SetEnhMetaFile](#setenhmetafile)設定之增強型中繼檔的控制碼。|
|[CStatic::GetIcon](#geticon)|抓取先前以[SetIcon](#seticon)設定之圖示的控制碼。|
|[CStatic::SetBitmap](#setbitmap)|指定要在靜態控制項中顯示的點陣圖。|
|[CStatic::SetCursor](#setcursor)|指定要在靜態控制項中顯示的游標影像。|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|指定要在靜態控制項中顯示的增強型中繼檔。|
|[CStatic::SetIcon](#seticon)|指定要在靜態控制項中顯示的圖示。|

## <a name="remarks"></a>備註

靜態控制項會顯示文字字串、方塊、矩形、圖示、游標、點陣圖或增強型中繼檔。 它可以用來標記、方塊或分隔其他控制項。 靜態控制項通常不會使用任何輸入, 而且不會提供輸出;不過, 如果是使用 SS_NOTIFY 樣式來建立, 它可以通知其父系按一下滑鼠。

以兩個步驟建立靜態控制項。 首先, 呼叫函式來建立`CStatic`物件, 然後呼叫[create](#create)成員函式來建立靜態控制項, 並`CStatic`將它附加至物件。

如果您在對話方塊`CStatic`中建立物件 (透過對話資源) `CStatic` , 當使用者關閉對話方塊時, 就會自動終結物件。

如果您在視窗`CStatic`中建立物件, 您可能也需要將它摧毀。 在視窗內的堆疊上建立的物件會自動終結。`CStatic` 如果您使用`CStatic` **新**的函式在堆積上建立物件, 您必須在物件上呼叫**delete** , 以在完成作業時將其摧毀。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="create"></a>CStatic:: Create

建立 Windows 靜態控制項, 並將它附加至`CStatic`物件。

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
指定要在控制項中放置的文字。 如果是 Null, 則不會顯示任何文字。

*dwStyle*<br/>
指定靜態控制項的視窗樣式。 將任何[靜態控制項樣式](../../mfc/reference/styles-used-by-mfc.md#static-styles)的組合套用至控制項。

*rect*<br/>
指定靜態控制項的位置和大小。 它可以`RECT`是結構`CRect`或物件。

*pParentWnd*<br/>
指定父視窗, 通常是`CDialog`物件。 `CStatic` 不得為 Null。

*nID*<br/>
指定靜態控制項的控制項 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

以兩個步驟來建立物件。`CStatic` 首先, 呼叫此`CStatic`函式, 然後呼叫`Create`, 它會建立 Windows 靜態控制項, `CStatic`並將它附加至物件。

將下列[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)套用至靜態控制項:

- WS_CHILD 一律

- WS_VISIBLE 通常

- WS_DISABLED 很少

如果您要在靜態控制項中顯示點陣圖、游標、圖示或中繼檔, 您必須套用下列其中一個[靜態樣式](../../mfc/reference/styles-used-by-mfc.md#static-styles):

- SS_BITMAP 將此樣式用於點陣圖。

- SS_ICON 將此樣式用於資料指標和圖示。

- SS_ENHMETAFILE 將此樣式用於增強型中繼檔。

針對資料指標、點陣圖或圖示, 您可能也會想要使用下列樣式:

- SS_CENTERIMAGE 用來將影像置中在靜態控制項中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

##  <a name="cstatic"></a>CStatic::CStatic

建構 `CStatic` 物件。

```
CStatic();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

##  <a name="drawitem"></a>CStatic::D rawItem

由架構呼叫以繪製主控描繪的靜態控制項。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的指標。 結構包含要繪製之專案的相關資訊, 以及所需的繪圖類型。

### <a name="remarks"></a>備註

覆寫此函式以實作為主控描繪`CStatic`物件的繪圖 (控制項的樣式為 SS_OWNERDRAW)。

##  <a name="getbitmap"></a>CStatic::GetBitmap

取得與[SetBitmap](#setbitmap)相關聯之`CStatic`點陣圖的控制碼 (先前已設定)。

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>傳回值

目前點陣圖的控制碼, 如果未設定任何點陣圖, 則為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="getcursor"></a>CStatic::GetCursor

取得與相關聯之`CStatic`資料指標的控制碼, 先前已設定[SetCursor](#setcursor)。

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>傳回值

目前資料指標的控制碼, 如果未設定任何資料指標, 則為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="getenhmetafile"></a>CStatic::GetEnhMetaFile

取得與相關聯之`CStatic`增強型中繼檔的控制碼, 先前已設定[SetEnhMetafile](#setenhmetafile)。

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>傳回值

目前增強型中繼檔的控制碼, 如果未設定任何增強型中繼檔, 則為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="geticon"></a>CStatic::GetIcon

取得與相關聯`CStatic`的圖示的控制碼, 先前以[SetIcon](#seticon)設定。

```
HICON GetIcon() const;
```

### <a name="return-value"></a>傳回值

目前圖示的控制碼, 如果未設定任何圖示則為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

##  <a name="setbitmap"></a>CStatic::SetBitmap

將新的點陣圖與靜態控制項產生關聯。

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
要在靜態控制項中繪製之點陣圖的控制碼。

### <a name="return-value"></a>傳回值

先前與靜態控制項相關聯之點陣圖的控制碼, 如果沒有與靜態控制項相關聯的點陣圖, 則為 Null。

### <a name="remarks"></a>備註

點陣圖會自動在靜態控制項中繪製。 根據預設, 它會在左上角繪製, 而靜態控制項則會調整為點陣圖的大小。

您可以使用各種視窗和靜態控制項樣式, 包括下列各項:

- SS_BITMAP 在點陣圖中一律使用此樣式。

- SS_CENTERIMAGE 用來將影像置中在靜態控制項中。 如果影像大於靜態控制項, 則會被裁剪。 如果小於靜態控制項, 則影像周圍的空白空間會以點陣圖左上角的圖元色彩填滿。

- MFC 提供類別, `CBitmap`當您必須使用點陣圖影像來執行更多工作, 而不只是呼叫`LoadBitmap`Win32 函式時, 您可以使用這個類別。 `CBitmap`, 其中包含一種 GDI 物件, 通常用於與`CStatic`進行合作, 這`CWnd`是用來將繪圖物件顯示為靜態控制項的類別。

`CImage`是一個 ATL/MFC 類別, 可讓您更輕鬆地使用與裝置無關的點陣圖 (DIB)。 如需詳細資訊, 請參閱[CImage 類別](../../atl-mfc-shared/reference/cimage-class.md)。

- 一般用法是提供`CStatic::SetBitmap`由`CBitmap`或`CImage`物件的 HBITMAP 運算子所傳回的 GDI 物件。 執行這項操作的程式碼與下面這一行類似。

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```
下列範例會在堆積`CStatic`上建立兩個物件。 接著, 它會使用來`CBitmap::LoadOEMBitmap`載入一個具有系統點陣圖的, 另一個則使用。 `CImage::Load`

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="setcursor"></a>  CStatic::SetCursor

將新的資料指標影像與靜態控制項產生關聯。

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>參數

*hCursor*<br/>
要在靜態控制項中繪製之游標的控制碼。

### <a name="return-value"></a>傳回值

先前與靜態控制項相關聯之資料指標的控制碼, 如果沒有與靜態控制項相關聯的資料指標, 則為 Null。

### <a name="remarks"></a>備註

游標會自動在靜態控制項中繪製。 根據預設, 它會在左上角繪製, 而靜態控制項則會調整為游標的大小。

您可以使用各種視窗和靜態控制項樣式, 包括下列各項:

- SS_ICON 對於資料指標和圖示一律使用此樣式。

- SS_CENTERIMAGE: 用來在靜態控制項中置中。 如果影像大於靜態控制項, 則會被裁剪。 如果小於靜態控制項, 則會以靜態控制項的背景色彩填滿影像周圍的空白空間。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="setenhmetafile"></a>  CStatic::SetEnhMetaFile

將新的增強型中繼檔影像與靜態控制項產生關聯。

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>參數

*hMetaFile*<br/>
要在靜態控制項中繪製之增強型中繼檔的控制碼。

### <a name="return-value"></a>傳回值

先前與靜態控制項相關聯之增強型中繼檔的控制碼, 如果沒有與靜態控制項相關聯的增強型中繼檔, 則為 Null。

### <a name="remarks"></a>備註

增強型中繼檔會自動在靜態控制項中繪製。 增強型中繼檔會調整以符合靜態控制項的大小。

您可以使用各種視窗和靜態控制項樣式, 包括下列各項:

- SS_ENHMETAFILE 使用此樣式一律適用于增強型中繼檔。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="seticon"></a>CStatic::SetIcon

將新的圖示影像與靜態控制項產生關聯。

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>參數

*hIcon*<br/>
要在靜態控制項中繪製之圖示的控制碼。

### <a name="return-value"></a>傳回值

先前與靜態控制項相關聯之圖示的控制碼, 如果沒有與靜態控制項相關聯的圖示, 則為 Null。

### <a name="remarks"></a>備註

圖示會自動在靜態控制項中繪製。 根據預設, 它會在左上角繪製, 而靜態控制項則會調整為圖示的大小。

您可以使用各種視窗和靜態控制項樣式, 包括下列各項:

- SS_ICON 對於資料指標和圖示一律使用此樣式。

- SS_CENTERIMAGE: 用來在靜態控制項中置中。 如果影像大於靜態控制項, 則會被裁剪。 如果小於靜態控制項, 則會以靜態控制項的背景色彩填滿影像周圍的空白空間。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit 類別](../../mfc/reference/cedit-class.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
