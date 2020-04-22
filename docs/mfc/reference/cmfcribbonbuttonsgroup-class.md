---
title: CMFCRibbonButtonsGroup 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButtons
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetCount
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetImageSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetRegularSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::HasImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::OnDrawImage
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::RemoveAll
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetParentCategory
helpviewer_keywords:
- CMFCRibbonButtonsGroup [MFC], CMFCRibbonButtonsGroup
- CMFCRibbonButtonsGroup [MFC], AddButton
- CMFCRibbonButtonsGroup [MFC], AddButtons
- CMFCRibbonButtonsGroup [MFC], GetButton
- CMFCRibbonButtonsGroup [MFC], GetCount
- CMFCRibbonButtonsGroup [MFC], GetImageSize
- CMFCRibbonButtonsGroup [MFC], GetRegularSize
- CMFCRibbonButtonsGroup [MFC], HasImages
- CMFCRibbonButtonsGroup [MFC], OnDrawImage
- CMFCRibbonButtonsGroup [MFC], RemoveAll
- CMFCRibbonButtonsGroup [MFC], SetImages
- CMFCRibbonButtonsGroup [MFC], SetParentCategory
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
ms.openlocfilehash: d690e8bf306234e7b742a4c6a0917e5430d92d10
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754110"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup 類別

該`CMFCRibbonButtonsGroup`類允許您將一組功能區按鈕組織到組中。 群組中的所有按鈕彼此水平直接相鄰，而且以框線框住。

## <a name="syntax"></a>語法

```
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|建構 `CMFCRibbonButtonsGroup` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC功能功能按鈕組::添加按鈕](#addbutton)|向組添加按鈕。|
|[CMFC功能功能按鈕組:新增按鈕](#addbuttons)|將按鈕清單添加到組。|
|[CMFC功能功能按鈕組:取得按鈕](#getbutton)|返回指向位於指定索引的按鈕的指標。|
|[CMFC功能中心按鈕組:取得計數](#getcount)|返回組中的按鈕數。|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|傳回功能區列中正常影像的影像大小(覆寫[CMFCRibbonBase 元素::抓取影像大小](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize)。|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|傳回功能區元素的一般大小(覆寫[CMFC 功能基礎元素::取得一般大小](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|報告`CMFCRibbonButtonsGroup`物件是否包含工具列圖像。|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|根據按鈕是正常、突出顯示還是禁用,為指定的按鈕繪製相應的圖像。|
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|從`CMFCRibbonButtonsGroup`物件中刪除所有按鈕。|
|[CMFC功能功能按鈕組::設定影像](#setimages)|將圖像分配給組。|
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|設定`CMFCRibbonButtonsGroup`物件的`CMFCRibbonCategory`父 級及其內的所有按鈕(覆寫[CMFC 功能基礎元素::設定父項目類別](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory)。|

## <a name="remarks"></a>備註

該組派生自[CMFCBaseRibbonElement,](../../mfc/reference/cmfcribbonbaseelement-class.md)可以作為單個實體進行操作。 您可以將組放置在任何面板或彈出功能表上。

## <a name="example"></a>範例

下例示範如何在 `CMFCRibbonButtonsGroup` 類別中使用各種方法。 該示例演示如何構造`CMFCRibbonButtonsGroup`物件、將圖像分配給功能區按鈕組以及向功能區按鈕組添加按鈕。 這段程式碼片段是 [Draw 用戶端範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>需求

**標題:** afxribbon 按鈕組.h

## <a name="cmfcribbonbuttonsgroupaddbutton"></a><a name="addbutton"></a>CMFC功能功能按鈕組::添加按鈕

向組添加按鈕。

```cpp
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>參數

*pButton*<br/>
[在]指向要添加的按鈕的指標。

## <a name="cmfcribbonbuttonsgroupaddbuttons"></a><a name="addbuttons"></a>CMFC功能功能按鈕組:新增按鈕

將按鈕清單添加到組。

```cpp
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>參數

*LstButtons*<br/>
[在]指向要添加的按鈕的指標清單。

## <a name="cmfcribbonbuttonsgroupcmfcribbonbuttonsgroup"></a><a name="cmfcribbonbuttonsgroup"></a>CMFC功能中心按鈕組:CMFC功能功能按鈕組

建構 `CMFCRibbonButtonsGroup` 物件。

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>參數

*pButton*<br/>
[在]指定要添加到新創建`CMFCRibbonButtonsGroup`的物件的按鈕。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonbuttonsgroupgetbutton"></a><a name="getbutton"></a>CMFC功能功能按鈕組:取得按鈕

返回指向位於指定索引的按鈕的指標。

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>參數

*I.*<br/>
[在]要返回的按鈕的零基索引。

### <a name="return-value"></a>傳回值

指向位於指定索引的按鈕的指標。 如果指定的索引範圍不一,則為 NULL。

### <a name="remarks"></a>備註

## <a name="cmfcribbonbuttonsgroupgetcount"></a><a name="getcount"></a>CMFC功能中心按鈕組:取得計數

返回組中的按鈕數。

```
int GetCount() const;
```

### <a name="return-value"></a>傳回值

組中的按鈕數。

## <a name="cmfcribbonbuttonsgroupgetimagesize"></a><a name="getimagesize"></a>CMFC 功能按鈕群組:抓取影像大小

檢索受保護`CMFCToolBarImages``m_Images`成員的源映射大小。

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>傳回值

返回工具列圖像的源圖像大小(如果存在)或`CSize`零(如果沒有)。

### <a name="remarks"></a>備註

## <a name="cmfcribbonbuttonsgroupgetregularsize"></a><a name="getregularsize"></a>CMFC 功能按鈕群組:取得一般大小

檢索功能區組元素的最大可能大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向功能區組的設備上下文。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonbuttonsgrouphasimages"></a><a name="hasimages"></a>CMFC功能中心按鈕組::有圖像

報告`CMFCRibbonButtonsGroup`物件是否包含工具列圖像。

```
BOOL HasImages() const;
```

### <a name="return-value"></a>傳回值

如果受保護`CMFCToolBarImages``m_Images`成員 包含任何圖像,則返回 TRUE;如果不包含,則返回 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcribbonbuttonsgroupondrawimage"></a><a name="ondrawimage"></a>CMFC功能中心按鈕組::在DrawImage上

根據按鈕是正常、突出顯示還是禁用,為指定的按鈕繪製相應的圖像。

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向`CMFCRibbonButtonsGroup`物件的設備上下文的指標。

*rectImage*<br/>
[在]要在其中繪製圖像的矩形。

*pButton*<br/>
[在]為其繪製圖像的按鈕。

*n 影像索引*<br/>
[在]要在按鈕上繪製的圖像索引(在用於正常、突出顯示或禁用按鈕的三個圖像陣列之一中)。

### <a name="remarks"></a>備註

## <a name="cmfcribbonbuttonsgroupremoveall"></a><a name="removeall"></a>CMFC功能功能按鈕組::刪除所有

從`CMFCRibbonButtonsGroup`物件中刪除所有按鈕。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>備註

## <a name="cmfcribbonbuttonsgroupsetimages"></a><a name="setimages"></a>CMFC功能功能按鈕組::設定影像

將圖像分配給功能區按鈕組。

```cpp
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>參數

*pImage*<br/>
[在]常規圖像。

*pHotImages*<br/>
[在]熱門圖像。

*p 關閉影像*<br/>
[在]已禁用的圖像。

### <a name="remarks"></a>備註

在`SetImages`將按鈕添加到組之前調用。 圖像數必須大於或等於要添加到組中的按鈕數。

> [!NOTE]
> 熱圖像是當使用者懸停在按鈕上時顯示的圖像。 禁用的圖像是禁用按鈕時顯示的圖像。

## <a name="cmfcribbonbuttonsgroupsetparentcategory"></a><a name="setparentcategory"></a>CMFC 功能按鈕組::設定父項目類別

設置`CMFCRibbonButtonsGroup`物件的`CMFCRibbonCategory`父 級及其內的所有按鈕。

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>參數

*p 類別*<br/>
[在]指向要設置的父類別(功能區控件中的選項卡式組稱為類別)。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
