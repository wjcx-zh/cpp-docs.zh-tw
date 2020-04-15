---
title: CMFCPropertyPage 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: e493f016b6384a768935186c31e3fc71ade6382f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361761"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage 類別

該`CMFCPropertyPage`類支援在屬性頁上顯示彈出式功能表。

## <a name="syntax"></a>語法

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC屬性頁:CMFC屬性頁](#cmfcpropertypage)|建構 `CMFCPropertyPage` 物件。|
|`CMFCPropertyPage::~CMFCPropertyPage`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCPropertyPage::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|`CMFCPropertyPage::OnSetActive`|當用戶選擇頁面並成為活動頁時,框架將調用此成員函數。 (覆寫[C 屬性頁:開啟活動](../../mfc/reference/cpropertypage-class.md#onsetactive).)|
|`CMFCPropertyPage::PreTranslateMessage`|在視窗訊息發送到[翻譯訊息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[調度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)視窗功能之前進行翻譯。 有關詳細資訊和方法語法,請參閱[CWnd::P重新翻譯消息](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CPropertyPage::PreTranslateMessage`。)|

## <a name="remarks"></a>備註

類`CMFCPropertyPage`表示屬性表的各個頁面,也稱為選項卡對話方塊。

將類`CMFCPropertyPage`與[CMFC 屬性表](../../mfc/reference/cmfcpropertysheet-class.md)類一起使用。 要在屬性頁上使用功能表,請將`CPropertyPage`類的所有匹配項替換為類。 `CMFCPropertyPage`

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>需求

**標題:** afx屬性頁.h

## <a name="cmfcpropertypagecmfcpropertypage"></a><a name="cmfcpropertypage"></a>CMFC屬性頁:CMFC屬性頁

建構 `CMFCPropertyPage` 物件。

```
CMFCPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption=0);

CMFCPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption=0);
```

### <a name="parameters"></a>參數

*nIDTemplate*<br/>
此頁範本的資源 ID。

*nIDCaption*<br/>
要放入此頁選項卡中的標籤的資源 ID。 如果為 0,則從此頁面的對話框範本中獲取該名稱。 預設值為 0。

*lpszTemplate 名稱*<br/>
指向此頁面的範本名稱。 不能是 NULL。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

有關建構函數參數的詳細資訊,請參閱[CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet 類別](../../mfc/reference/cmfcpropertysheet-class.md)
