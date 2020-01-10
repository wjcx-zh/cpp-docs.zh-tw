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
ms.openlocfilehash: 4be584135ef789d7fbe3b1743ac0ad6ce66ac5b1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505034"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage 類別

`CMFCPropertyPage`類別支援在屬性頁上顯示快顯功能表。

## <a name="syntax"></a>語法

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|建構 `CMFCPropertyPage` 物件。|
|`CMFCPropertyPage::~CMFCPropertyPage`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCPropertyPage::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|`CMFCPropertyPage::OnSetActive`|當使用者選擇頁面時，架構會呼叫這個成員函式，並成為使用中的頁面。 （覆寫[CPropertyPage：： OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive)。）|
|`CMFCPropertyPage::PreTranslateMessage`|會先轉譯視窗訊息，再將它們分派至[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函式。 如需詳細資訊和方法語法，請參閱[CWnd：:P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 (覆寫 `CPropertyPage::PreTranslateMessage`。)|

## <a name="remarks"></a>備註

`CMFCPropertyPage`類別代表屬性工作表的個別頁面，也稱為索引標籤對話方塊。

將類別與 [CMFCPropertySheet ](../../mfc/reference/cmfcpropertysheet-class.md) 類別搭配使用。`CMFCPropertyPage` 若要在屬性頁上使用功能表，請以`CPropertyPage` `CMFCPropertyPage`類別取代所有出現的類別。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>需求

**標頭：** afxpropertypage。h

##  <a name="cmfcpropertypage"></a>CMFCPropertyPage：： CMFCPropertyPage

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
此頁面範本的資源識別碼。

*nIDCaption*<br/>
要放入此頁面索引標籤中之標籤的資源識別碼。 如果是0，則會從這個頁面的對話方塊範本取得名稱。 預設值為 0。

*lpszTemplateName*<br/>
指向此頁面的範本名稱。 不可以是 NULL。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

如需有關此函式參數的詳細資訊，請參閱[CPropertyPage：： CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet 類別](../../mfc/reference/cmfcpropertysheet-class.md)
