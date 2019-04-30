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
ms.openlocfilehash: cd657ac035c004e7aa9bfcd2f6dbd2f3c90da80c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410083"
---
# <a name="cmfcribbonundobutton-class"></a>CMFCRibbonUndoButton 類別

`CMFCRibbonUndoButton`類別實作，其中包含最新的使用者命令中的下拉式清單按鈕。 使用者可以選取一或多個最新的命令，從下拉式清單中，重做或復原。

## <a name="syntax"></a>語法

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|建構新`CMFCRibbonUndoButton`使用您指定的命令識別碼、 文字標籤和映像從映像清單中的父物件的物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|動作清單中加入新的動作。|
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|清除動作清單，也就是下拉式清單。|
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|判斷使用者從下拉式清單中選取的項目數目。|
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|指出物件是否包含一個功能表。|

## <a name="remarks"></a>備註

`CMFCRibbonUndoButton`類別使用堆疊來代表下拉式清單。

## <a name="example"></a>範例

下列範例示範如何建構的物件`CMFCRibbonUndoButton`類別，並將新的動作新增至動作的清單。 此程式碼片段是一部分[功能區小工具範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>需求

**標頭：** afxribbonundobutton.h

##  <a name="addundoaction"></a>  CMFCRibbonUndoButton::AddUndoAction

動作清單中加入新的動作。

```
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[in]動作標籤會顯示在下拉式清單中。

##  <a name="cleanupundolist"></a>  CMFCRibbonUndoButton::CleanUpUndoList

清除動作清單，也就是下拉式清單。

```
void CleanUpUndoList();
```

##  <a name="cmfcribbonundobutton"></a>  CMFCRibbonUndoButton::CMFCRibbonUndoButton

建構新`CMFCRibbonUndoButton`使用您指定的命令識別碼、 文字標籤和映像從映像清單中的父物件的物件。

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
[in]指定命令識別碼。

*lpszText*<br/>
[in]指定按鈕的文字標籤。

*nSmallImageIndex*<br/>
[in]影像清單中的按鈕的小型影像的父物件的以零為起始的索引。

*nLargeImageIndex*<br/>
[in]以零起始的索引中的父物件的影像清單的按鈕的大型影像。

*hIcon*<br/>
[in]您可以使用為按鈕的影像圖示控制代碼。

##  <a name="getactionnumber"></a>  CMFCRibbonUndoButton::GetActionNumber

判斷使用者從下拉式清單中選取的項目數目。

```
int GetActionNumber() const;
```

### <a name="return-value"></a>傳回值

使用者選取的項目數目。

##  <a name="hasmenu"></a>  CMFCRibbonUndoButton::HasMenu

指出物件是否包含一個功能表。

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>傳回值

一律會傳回 TRUE。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery 類別](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)
