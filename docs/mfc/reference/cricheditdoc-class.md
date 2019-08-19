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
ms.openlocfilehash: d296185fe2ea2216f4abe17b191f71b6fa36e1f9
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916715"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc 類別

使用[CRichEditView](../../mfc/reference/cricheditview-class.md)和[CRICHEDITCNTRITEM](../../mfc/reference/cricheditcntritem-class.md), 在 MFC 的檔視圖架構內容中提供 rich edit 控制項的功能。

## <a name="syntax"></a>語法

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|呼叫以執行檔的清除。|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|指出資料流程輸入和輸出是否應包含格式資訊。|
|[CRichEditDoc::GetView](#getview)|抓取 asssociated [CRichEditView](../../mfc/reference/cricheditview-class.md)物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|指出資料流程 i/o 是否應包含格式。|

## <a name="remarks"></a>備註

「Rich edit 控制項」是一種視窗, 使用者可以在其中輸入和編輯文字。 文字可以被指派字元和段落格式, 而且可以包含內嵌的 OLE 物件。 Rich edit 控制項會提供用來格式化文字的程式設計介面。 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。

`CRichEditView` 會維護文字和文字的格式特性。 `CRichEditDoc`維護在此視圖中的用戶端專案清單。 `CRichEditCntrItem`提供 OLE 用戶端專案的容器端存取權。

這個 Windows 通用控制項 (因此也就是[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相關類別) 僅適用于在 windows 95/98 和 windows NT 3.51 版和更新版本下執行的程式。

如需在 MFC 應用程式中使用 rich edit 檔的範例, 請參閱[WORDPAD](../../overview/visual-cpp-samples.md)範例應用程式。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>需求

**標頭:** afxrich。h

##  <a name="createclientitem"></a>CRichEditDoc:: CreateClientItem

呼叫此函式以建立`CRichEditCntrItem`物件, 並將它新增至此檔。

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>參數

*preo*<br/>
描述 OLE 專案之[REOBJECT](/windows/desktop/api/richole/ns-richole-reobject)結構的指標。 新`CRichEditCntrItem`的物件是以這個 OLE 專案為圍繞。 如果*preo*為 Null, 新的用戶端專案會是空的。

### <a name="return-value"></a>傳回值

已加入此檔的新[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)物件的指標。

### <a name="remarks"></a>備註

此函式不會執行任何 OLE 初始化。

如需詳細資訊, 請參閱 Windows SDK 中的[REOBJECT](/windows/desktop/api/richole/ns-richole-reobject)結構。

##  <a name="getstreamformat"></a>CRichEditDoc:: GetStreamFormat

呼叫此函式可判斷用來串流豐富編輯內容的文字格式。

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>傳回值

下列其中一個旗標:

- SF_TEXT 表示 rich edit 控制項不會維護格式資訊。

- SF_RTF 表示 rich edit 控制項確實會維護格式資訊。

### <a name="remarks"></a>備註

傳回值是以[m_bRTF](#m_brtf)資料成員為基礎。 如果`m_bRTF`為 TRUE, 則此函式會傳回 SF_RTF, 否則會傳回 SF_TEXT。

##  <a name="getview"></a>CRichEditDoc:: GetView

呼叫此函式可存取與這個`CRichEditDoc`物件相關聯的 [CRichEditView](../../mfc/reference/cricheditview-class.md) 物件。

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>傳回值

與檔相關`CRichEditView`聯之物件的指標。

### <a name="remarks"></a>備註

文字和格式設定資訊都包含在`CRichEditView`物件中。 `CRichEditDoc`物件會維護用於序列化的 OLE 專案。 每個`CRichEditView` `CRichEditDoc`只能有一個。

##  <a name="m_brtf"></a>CRichEditDoc:: m_bRTF

當為 TRUE 時, 表示[CRichEditCtrl:: StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin)和[CRichEditCtrl:: StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout)應儲存段落和字元格式特性。

```
BOOL m_bRTF;
```

## <a name="see-also"></a>另請參閱

[MFC 範例 WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRichEditView 類別](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem 類別](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument 類別](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl 類別](../../mfc/reference/cricheditctrl-class.md)
