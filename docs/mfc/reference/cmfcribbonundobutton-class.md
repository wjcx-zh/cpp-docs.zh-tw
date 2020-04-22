---
title: CMFCRibbonUndoButton 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
ms.openlocfilehash: 15cf93d39057f0e235779d47cf24d920d80a807d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753489"
---
# <a name="cmfcribbonundobutton-class"></a>CMFCRibbonUndoButton 類別

類`CMFCRibbonUndoButton`實現包含最新使用者命令的下拉清單按鈕。 用戶可以從下拉清單中選擇一個或多個最新命令,以重做或撤銷這些命令。

## <a name="syntax"></a>語法

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC 功能Undo按鈕::CMFC功能放大縮小字體功能](#cmfcribbonundobutton)|使用指定的命令`CMFCRibbonUndoButton`ID、文本標籤和父物件的圖像清單中的圖像來建構新物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC 功能Undo按鈕::添加UndoAction](#addundoaction)|加入操作清單加入新操作。|
|[CMFC 功能整理按鈕::清除 Undo 清單](#cleanupundolist)|清除操作清單,這是下拉清單。|
|[CMFC 功能Undo按鈕:取得操作編號](#getactionnumber)|確定使用者從下拉清單中選擇的項數。|
|[CMFC 功能放大縮小字型功能 放大縮小字型功能](#hasmenu)|指示物件是否包含功能表。|

## <a name="remarks"></a>備註

類`CMFCRibbonUndoButton`使用堆疊來表示下拉清單。

## <a name="example"></a>範例

下面的範例展示如何建構`CMFCRibbonUndoButton`類的物件,以及如何向操作清單中添加新操作。 此代碼段是[功能區小工具示例的一](../../overview/visual-cpp-samples.md)部分。

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>需求

**標題:** afxribbonundobutton.h

## <a name="cmfcribbonundobuttonaddundoaction"></a><a name="addundoaction"></a>CMFC 功能Undo按鈕::添加UndoAction

加入操作清單加入新操作。

```cpp
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[在]將在下拉清單中顯示的操作標籤。

## <a name="cmfcribbonundobuttoncleanupundolist"></a><a name="cleanupundolist"></a>CMFC 功能整理按鈕::清除 Undo 清單

清除操作清單,這是下拉清單。

```cpp
void CleanUpUndoList();
```

## <a name="cmfcribbonundobuttoncmfcribbonundobutton"></a><a name="cmfcribbonundobutton"></a>CMFC 功能Undo按鈕::CMFC功能放大縮小字體功能

使用指定的命令`CMFCRibbonUndoButton`ID、文本標籤和父物件的圖像清單中的圖像來建構新物件。

```
CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex=-1,
    int nLargeImageIndex=-1);

CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    HICON hIcon);
```

### <a name="parameters"></a>參數

*nID*<br/>
[在]指定命令識別碼。

*lpszText*<br/>
[在]指定按鈕的文字標籤。

*n 小圖像索引*<br/>
[在]按鈕小圖像的父物件圖像清單中的零索引。

*nLargeImageIndex*<br/>
[在]按鈕大圖像的父物件圖像清單中的零索引。

*hIcon*<br/>
[在]圖示的句柄,您可以將其用作按鈕的圖像。

## <a name="cmfcribbonundobuttongetactionnumber"></a><a name="getactionnumber"></a>CMFC 功能Undo按鈕:取得操作編號

確定使用者從下拉清單中選擇的項數。

```
int GetActionNumber() const;
```

### <a name="return-value"></a>傳回值

用戶選擇的項數。

## <a name="cmfcribbonundobuttonhasmenu"></a><a name="hasmenu"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

指示物件是否包含功能表。

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>傳回值

始終返回 TRUE。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery 類別](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)
