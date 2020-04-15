---
title: CMFCRibbonGalleryMenuButton 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CopyFrom
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CreatePopupMenu
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::GetPalette
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::HasButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed
helpviewer_keywords:
- CMFCRibbonGalleryMenuButton [MFC], CMFCRibbonGalleryMenuButton
- CMFCRibbonGalleryMenuButton [MFC], CopyFrom
- CMFCRibbonGalleryMenuButton [MFC], CreatePopupMenu
- CMFCRibbonGalleryMenuButton [MFC], GetPalette
- CMFCRibbonGalleryMenuButton [MFC], HasButton
- CMFCRibbonGalleryMenuButton [MFC], IsEmptyMenuAllowed
ms.assetid: 4d459d9b-8b1a-4371-92f6-dc4ce6cc42c8
ms.openlocfilehash: 305393def3b176b052b1db89c66c1e755f528ee6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375135"
---
# <a name="cmfcribbongallerymenubutton-class"></a>CMFCRibbonGalleryMenuButton 類別

實作包含功能區組件庫的功能區功能表按鈕。
有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCRibbonGalleryMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton](#cmfcribbongallerymenubutton)|建構並初始化 `CMFCRibbonGalleryMenuButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonGalleryMenuButton::CopyFrom](#copyfrom)|(覆蓋[CMFCToolBarMenu 按鈕::從](../../mfc/reference/cmfctoolbarmenubutton-class.md#copyfrom)複製。|
|[CMFCRibbonGalleryMenuButton::CreatePopupMenu](#createpopupmenu)|(覆蓋[CMFCToolBarMenu 按鈕::建立彈出選單](../../mfc/reference/cmfctoolbarmenubutton-class.md#createpopupmenu).)|
|[CMFCRibbonGalleryMenuButton::GetPalette](#getpalette)||
|[CMFCRibbonGalleryMenuButton::HasButton](#hasbutton)|(覆寫 `CMFCToolBarMenuButton::HasButton`。)|
|[CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|(覆蓋[CMFCToolBarMenu 按鈕::是空門允許](../../mfc/reference/cmfctoolbarmenubutton-class.md#isemptymenuallowed).)|

### <a name="remarks"></a>備註

組件庫功能表按鈕會顯示成含箭頭的快顯功能表。 當使用者按一下此按鈕時，會顯示影像庫。 當您建構組件庫功能表按鈕時，您必須指定包含這些影像的影像清單。

## <a name="example"></a>範例

下列範例示範如何顯示功能表按鈕中項目符號的組件庫：

```cpp
BOOL CMainFrame::OnShowPopupMenu (CMFCPopupMenu* pMenuPopup)
{
    int nBulletIndex = pMenuBar->CommandToIndex (ID_PARA_BULLETS);

    if (nBulletIndex>= 0)
    {
        CMFCToolBarButton* pExButton =
        pMenuBar->GetButton(nBulletIndex);
        ASSERT_VALID (pExButton);

        CMFCRibbonGalleryMenuButton paletteBullet (
        pExButton->m_nID,
        pExButton->GetImage (),
        pExButton->m_strText);

        InitBulletPalette (&paletteBullet.GetPalette ());

        pMenuBar->ReplaceButton (ID_PARA_BULLETS,
        paletteBullet);
    }
}
```

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)\
•&nbsp;[CMFC 工具列按鈕](../../mfc/reference/cmfctoolbarbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CMFCToolBarMenu按鈕](../../mfc/reference/cmfctoolbarmenubutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CMFC 功能畫廊選單按鈕](../../mfc/reference/cmfcribbongallerymenubutton-class.md)

## <a name="requirements"></a>需求

**標題:** afxRibbonPaletteGallery.h

## <a name="cmfcribbongallerymenubuttoncopyfrom"></a><a name="copyfrom"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

[在]*斯爾克*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcribbongallerymenubuttoncmfcribbongallerymenubutton"></a><a name="cmfcribbongallerymenubutton"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

建構並初始化[CMFC 功能區GalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)物件。

```
CMFCRibbonGalleryMenuButton(
    UINT uiID,
    int iImage,
    LPCTSTR lpszText,
    CMFCToolBarImages& imagesPalette);

CMFCRibbonGalleryMenuButton(
    UINT uiID,
    int iImage,
    LPCTSTR lpszText,
    UINT uiImagesPaletteResID = 0,
    int cxPaletteImage = 0);
```

### <a name="parameters"></a>參數

*uiID*<br/>
按鈕的命令識別碼。 這是用戶按下此按鈕時在WM_COMMAND消息中發送的值。

*i 影像*<br/>
要使用庫功能表按鈕顯示的圖像索引。 圖像儲存在*圖像調色板*參數中。

*lpszText*<br/>
要顯示在功能表按鈕上的文本。

*影像調色盤*<br/>
包含要在庫中顯示的圖像清單。

*uiImagesPaletteResID*<br/>
要在庫中顯示的影像清單的資源識別碼。

*cxPalette影像*<br/>
指定要在庫中顯示的圖像的寬度(以像素為單位)。

### <a name="remarks"></a>備註

庫選單按鈕顯示為具有箭頭的彈出式功能表。 當使用者按一下此按鈕時，會顯示影像庫。

### <a name="example"></a>範例

下面的範例展示如何使用`CMFCRibbonGalleryMenuButton`類的構造函數。 此代碼段是 MS [Office 2007 演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#8](../../mfc/reference/codesnippet/cpp/cmfcribbongallerymenubutton-class_1.cpp)]

## <a name="cmfcribbongallerymenubuttoncreatepopupmenu"></a><a name="createpopupmenu"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbongallerymenubuttongetpalette"></a><a name="getpalette"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

```
CMFCRibbonGallery& GetPalette();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbongallerymenubuttonhasbutton"></a><a name="hasbutton"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

```
virtual BOOL HasButton() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbongallerymenubuttonisemptymenuallowed"></a><a name="isemptymenuallowed"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[CMFCRibbonGallery 類別](../../mfc/reference/cmfcribbongallery-class.md)
