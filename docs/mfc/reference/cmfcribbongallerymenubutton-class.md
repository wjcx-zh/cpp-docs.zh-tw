---
title: CMFCRibbonGalleryMenuButton 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CopyFrom
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CreatePopupMenu
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::GetPalette
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::HasButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonGalleryMenuButton [MFC], CMFCRibbonGalleryMenuButton
- CMFCRibbonGalleryMenuButton [MFC], CopyFrom
- CMFCRibbonGalleryMenuButton [MFC], CreatePopupMenu
- CMFCRibbonGalleryMenuButton [MFC], GetPalette
- CMFCRibbonGalleryMenuButton [MFC], HasButton
- CMFCRibbonGalleryMenuButton [MFC], IsEmptyMenuAllowed
ms.assetid: 4d459d9b-8b1a-4371-92f6-dc4ce6cc42c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1ddec12ccdd6fb730ac9f1c5170f17e52eede2b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448190"
---
# <a name="cmfcribbongallerymenubutton-class"></a>CMFCRibbonGalleryMenuButton 類別

實作包含功能區組件庫的功能區功能表按鈕。
如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

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
|[CMFCRibbonGalleryMenuButton::CopyFrom](#copyfrom)|(覆寫[cmfctoolbarmenubutton:: Copyfrom](../../mfc/reference/cmfctoolbarmenubutton-class.md#copyfrom)。)|
|[CMFCRibbonGalleryMenuButton::CreatePopupMenu](#createpopupmenu)|(覆寫[cmfctoolbarmenubutton:: Createpopupmenu](../../mfc/reference/cmfctoolbarmenubutton-class.md#createpopupmenu)。)|
|[CMFCRibbonGalleryMenuButton::GetPalette](#getpalette)||
|[CMFCRibbonGalleryMenuButton::HasButton](#hasbutton)|(覆寫 `CMFCToolBarMenuButton::HasButton`。)|
|[CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|(覆寫[cmfctoolbarmenubutton:: Isemptymenuallowed](../../mfc/reference/cmfctoolbarmenubutton-class.md#isemptymenuallowed)。)|

### <a name="remarks"></a>備註

組件庫功能表按鈕會顯示成含箭頭的快顯功能表。 當使用者按一下此按鈕時，會顯示影像庫。 當您建構組件庫功能表按鈕時，您必須指定包含這些影像的影像清單。

## <a name="example"></a>範例

下列範例示範如何顯示功能表按鈕中項目符號的組件庫：

```
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

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md) [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)

## <a name="requirements"></a>需求

**標頭：** afxRibbonPaletteGallery.h

##  <a name="copyfrom"></a>  CMFCRibbonGalleryMenuButton::CopyFrom


```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

[in]*src*

### <a name="remarks"></a>備註

##  <a name="cmfcribbongallerymenubutton"></a>  CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton

建構並初始化[CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)物件。

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
按鈕的命令識別碼。 這是當使用者按一下此按鈕傳送 WM_COMMAND 訊息中的值。

*iImage*<br/>
要與組件庫功能表按鈕一起顯示之影像的索引。 影像會儲存在*imagesPalette*參數。

*lpszText*<br/>
要顯示的功能表按鈕上的文字。

*imagesPalette*<br/>
包含要顯示在資源庫上的映像清單。

*uiImagesPaletteResID*<br/>
要顯示在資源庫映像的映像清單的資源識別碼。

*cxPaletteImage*<br/>
指定像素為單位的資源庫上顯示影像的寬度。

### <a name="remarks"></a>備註

組件庫功能表按鈕會顯示為快顯功能表有個箭號。 當使用者按一下此按鈕時，會顯示影像庫。

### <a name="example"></a>範例

下列範例示範如何使用的建構函式`CMFCRibbonGalleryMenuButton`類別。 此程式碼片段是一部分[MS Office 2007 示範範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MSOffice2007Demo#8](../../mfc/reference/codesnippet/cpp/cmfcribbongallerymenubutton-class_1.cpp)]

##  <a name="createpopupmenu"></a>  CMFCRibbonGalleryMenuButton::CreatePopupMenu


```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getpalette"></a>  CMFCRibbonGalleryMenuButton::GetPalette


```
CMFCRibbonGallery& GetPalette();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="hasbutton"></a>  CMFCRibbonGalleryMenuButton::HasButton


```
virtual BOOL HasButton() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isemptymenuallowed"></a>  CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed


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
