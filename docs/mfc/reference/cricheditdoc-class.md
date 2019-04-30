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
ms.openlocfilehash: 4cc3af7649d30a153b67cd8269e595c11018833f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372084"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc 類別

具有[CRichEditView](../../mfc/reference/cricheditview-class.md)並[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)，提供 rich edit 控制項的 MFC 的文件檢視架構內容中的功能。

## <a name="syntax"></a>語法

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|呼叫以執行清除作業的文件。|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|指出資料流輸入和輸出是否應該包含格式資訊。|
|[CRichEditDoc::GetView](#getview)|擷取有關聯[CRichEditView](../../mfc/reference/cricheditview-class.md)物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|指出資料流 I/O 是否應包含格式設定。|

## <a name="remarks"></a>備註

「 Rich edit 控制項 」 是一個視窗，讓使用者輸入及編輯文字。 文字字元和段落格式，可指派，而且可以包含內嵌的 OLE 物件。 Rich edit 控制項的格式化文字，提供程式設計介面。 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。

`CRichEditView` 會維護文字和文字的格式特性。 `CRichEditDoc` 會維護用戶端項目，也就是在檢視中的清單。 `CRichEditCntrItem` 提供 OLE 用戶端項目容器端存取。

這個 Windows 通用控制項 (因而[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相關類別) 僅適用於 Windows 95/98 和 Windows NT 的版本 3.51 下執行的程式和更新版本。

在 MFC 應用程式中使用豐富的編輯文件的範例，請參閱[WORDPAD](../../overview/visual-cpp-samples.md)範例應用程式。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>需求

**標頭：** afxrich.h

##  <a name="createclientitem"></a>  CRichEditDoc::CreateClientItem

呼叫此函式可建立`CRichEditCntrItem`物件，並將它新增至這份文件。

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>參數

*preo*<br/>
指標[REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject)結構描述 OLE 項目。 新`CRichEditCntrItem`物件會建構這個 OLE 項目。 如果*preo*是 NULL，新的用戶端項目是空的。

### <a name="return-value"></a>傳回值

新指標[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)已新增至這份文件物件。

### <a name="remarks"></a>備註

此函式不會執行任何 OLE 初始化。

如需詳細資訊，請參閱 < [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) Windows SDK 中的結構。

##  <a name="getstreamformat"></a>  CRichEditDoc::GetStreamFormat

呼叫此函式來判斷文字格式進行串流處理的豐富的編輯內容。

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>傳回值

其中一個下列旗標：

- SF_TEXT 指出 rich edit 控制項不會維護格式資訊。

- SF_RTF 指出 rich edit 控制項沒有維護格式資訊。

### <a name="remarks"></a>備註

傳回值根據[m_bRTF](#m_brtf)資料成員。 如果此函數會傳回 SF_RTF `m_bRTF` ，則為 TRUE; 否則即為 SF_TEXT。

##  <a name="getview"></a>  CRichEditDoc::GetView

呼叫此函式來存取[CRichEditView](../../mfc/reference/cricheditview-class.md)與此相關聯的物件`CRichEditDoc`物件。

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>傳回值

指標`CRichEditView`文件相關聯的物件。

### <a name="remarks"></a>備註

文字和格式設定資訊都包含在`CRichEditView`物件。 `CRichEditDoc`物件會維護 OLE 項目，進行序列化。 應該只有一個`CRichEditView`針對每個`CRichEditDoc`。

##  <a name="m_brtf"></a>  CRichEditDoc::m_bRTF

若為 TRUE，表示[CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin)並[CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout)應該儲存段落和字元格式的特性。

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
