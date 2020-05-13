---
title: CRichEditDoc 類別
ms.date: 11/04/2016
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
ms.openlocfilehash: 587cf65543e24e586fb8b2336481d6e841473134
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368266"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc 類別

使用[CRichEditView](../../mfc/reference/cricheditview-class.md)和[CRichEdit CntrItem,](../../mfc/reference/cricheditcntritem-class.md)在 MFC 的文檔視圖體系結構上下文中提供了豐富的編輯控制項的功能。

## <a name="syntax"></a>語法

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[克里希編輯文件:建立用戶端項目](#createclientitem)|調用 以執行文檔的清理。|
|[克里希編輯文件:取得串流格式](#getstreamformat)|指示流輸入和輸出是否應包含格式設定資訊。|
|[克里希編輯文件:取得檢視](#getview)|檢索同化[CRichEditView](../../mfc/reference/cricheditview-class.md)物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[克里希編輯文件:m_bRTF](#m_brtf)|指示流 I/O 是否應包含格式。|

## <a name="remarks"></a>備註

"富編輯控制件"是使用者可以在其中輸入和編輯文本的視窗。 文本可以分配字元和段落格式,並可以包括嵌入的 OLE 物件。 豐富的編輯控制項為文字格式設定提供了程式設計介面。 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。

`CRichEditView` 會維護文字和文字的格式特性。 `CRichEditDoc`維護檢視中的用戶端項的清單。 `CRichEditCntrItem`提供對 OLE 用戶端項的容器端訪問。

此 Windows 通用控件(因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相關類)僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下運行的程式。

有關在 MFC 應用程式中使用富編輯文檔的範例,請參閱[WORDPAD](../../overview/visual-cpp-samples.md)範例應用程式。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>需求

**標題:** afxrich.h

## <a name="cricheditdoccreateclientitem"></a><a name="createclientitem"></a>克里希編輯文件:建立用戶端項目

呼叫此函數以創建物件`CRichEditCntrItem`並將其添加到此文檔。

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>參數

*普雷奧*<br/>
指向描述 OLE 項的[REOBJECT](/windows/win32/api/richole/ns-richole-reobject)結構的指標。 新`CRichEditCntrItem`物件圍繞此 OLE 項構造。 如果*Preo*為 NULL,則新用戶端項為空。

### <a name="return-value"></a>傳回值

指向已新增到文件的新[CRichEditCntrItem 物件](../../mfc/reference/cricheditcntritem-class.md)。

### <a name="remarks"></a>備註

此功能不執行任何 OLE 初始化。

有關詳細資訊,請參閱 Windows SDK 中的[REOBJECT](/windows/win32/api/richole/ns-richole-reobject)結構。

## <a name="cricheditdocgetstreamformat"></a><a name="getstreamformat"></a>克里希編輯文件:取得串流格式

呼叫此函數以確定流豐富的編輯內容的文本格式。

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>傳回值

以下標誌之一:

- SF_TEXT 指示富編輯控件不維護格式設置資訊。

- SF_RTF指示富編輯控件確實維護格式資訊。

### <a name="remarks"></a>備註

返回值基於[m_bRTF](#m_brtf)數據成員。 如果`m_bRTF`為 TRUE,則此函數將返回SF_RTF;否則,SF_TEXT。

## <a name="cricheditdocgetview"></a><a name="getview"></a>克里希編輯文件:取得檢視

調用此函數以造訪與`CRichEditDoc`此 物件關聯的[CRichEditView](../../mfc/reference/cricheditview-class.md)物件。

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>傳回值

指向與文件`CRichEditView`關聯的物件的指標。

### <a name="remarks"></a>備註

文字與格式資訊包含在物件中`CRichEditView`。 物件`CRichEditDoc`維護用於序列化的 OLE 項。 每個`CRichEditDoc`應該只有一`CRichEditView`個 。

## <a name="cricheditdocm_brtf"></a><a name="m_brtf"></a>克里希編輯文件:m_bRTF

當 TRUE 時,指示[CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin)和[CRichEditCtrl::Streamout](../../mfc/reference/cricheditctrl-class.md#streamout)應儲存段落和字元格式特徵。

```
BOOL m_bRTF;
```

## <a name="see-also"></a>另請參閱

[MFC 樣品 WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRichEditView 類別](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem 類別](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument 類別](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl 類別](../../mfc/reference/cricheditctrl-class.md)
