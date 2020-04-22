---
title: CRichEditCntrItem 類別
ms.date: 11/04/2016
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
ms.openlocfilehash: 7b566fe7f1c0667dbcdb4976f79cd2e1597f48f6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752764"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem 類別

使用[CRichEditView](../../mfc/reference/cricheditview-class.md)和[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md),在 MFC 的文檔檢視體系結構的上下文中提供了豐富的編輯控制件的功能。

## <a name="syntax"></a>語法

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[克里希編輯專案::克里希編輯Cntrtr專案](#cricheditcntritem)|建構 `CRichEditCntrItem` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[克里希編輯專案::同步到裡希編輯物件](#synctoricheditobject)|將該項目啟動為另一種類型。|

## <a name="remarks"></a>備註

"富編輯控制件"是使用者可以在其中輸入和編輯文本的視窗。 文本可以分配字元和段落格式,並可以包括嵌入的 OLE 物件。 豐富的編輯控制項為文字格式設定提供了程式設計介面。 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。

`CRichEditView` 會維護文字和文字的格式特性。 `CRichEditDoc`維護檢視中的 OLE 客戶端項的清單。 `CRichEditCntrItem` 提供 OLE 用戶端項目的存取權給容器端。

此 Windows 通用控件(因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相關類)僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下運行的程式。

有關在 MFC 應用程式中使用富編輯容器項的範例,請參閱[WORDPAD](../../overview/visual-cpp-samples.md)範例應用程式。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>需求

**標題:** afxrich.h

## <a name="cricheditcntritemcricheditcntritem"></a><a name="cricheditcntritem"></a>克里希編輯專案::克里希編輯Cntrtr專案

呼叫此函數以創建物件`CRichEditCntrItem`並將其添加到容器文檔。

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>參數

*普雷奧*<br/>
指向描述 OLE 項的[REOBJECT](/windows/win32/api/richole/ns-richole-reobject)結構的指標。 新`CRichEditCntrItem`物件圍繞此 OLE 項構造。 如果*Preo*為 NULL,則用戶端項為空。

*pContainer*<br/>
指向將包含此項的容器文件的指標。 如果*pContainer*為 NULL,則必須顯式調用[COleDocument::addItem](../../mfc/reference/coledocument-class.md#additem)才能將此用戶端項添加到文檔中。

### <a name="remarks"></a>備註

此功能不執行任何 OLE 初始化。

有關詳細資訊,請參閱 Windows SDK 中的[REOBJECT](/windows/win32/api/richole/ns-richole-reobject)結構。

## <a name="cricheditcntritemsynctoricheditobject"></a><a name="synctoricheditobject"></a>克里希編輯專案::同步到裡希編輯物件

呼叫此函數以將設備`CRichEditCntrltem`方面[DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)與*reo*指定的設備方面同步。

```cpp
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>參數

*雷奧*<br/>
引用描述 OLE 項的[REOBJECT](/windows/win32/api/richole/ns-richole-reobject)結構。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[DVASPECT。](/windows/win32/api/wtypes/ne-wtypes-dvaspect)

## <a name="see-also"></a>另請參閱

[MFC 樣品 WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc 類別](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView 類別](../../mfc/reference/cricheditview-class.md)
