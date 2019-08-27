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
ms.openlocfilehash: 8e242504c8ab0f59f6dec0602d4a5352a2d84867
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502719"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem 類別

使用[CRichEditView](../../mfc/reference/cricheditview-class.md)和[CRICHEDITDOC](../../mfc/reference/cricheditdoc-class.md), 在 MFC 的檔視圖架構內容中提供 rich edit 控制項的功能。

## <a name="syntax"></a>語法

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|建構 `CRichEditCntrItem` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|以另一種類型的形式啟動專案。|

## <a name="remarks"></a>備註

「Rich edit 控制項」是一種視窗, 使用者可以在其中輸入和編輯文字。 文字可以被指派字元和段落格式, 而且可以包含內嵌的 OLE 物件。 Rich edit 控制項會提供用來格式化文字的程式設計介面。 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。

`CRichEditView` 會維護文字和文字的格式特性。 `CRichEditDoc`維護在此視圖中的 OLE 用戶端專案清單。 `CRichEditCntrItem` 提供 OLE 用戶端項目的存取權給容器端。

這個 Windows 通用控制項 (因此也就是[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相關類別) 僅適用于在 windows 95/98 和 windows NT 3.51 版和更新版本下執行的程式。

如需在 MFC 應用程式中使用豐富編輯容器專案的範例, 請參閱[WORDPAD](../../overview/visual-cpp-samples.md)範例應用程式。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>需求

**標頭:** afxrich。h

##  <a name="cricheditcntritem"></a>CRichEditCntrItem:: CRichEditCntrItem

呼叫此函式以建立`CRichEditCntrItem`物件, 並將它加入至容器檔案。

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>參數

*preo*<br/>
描述 OLE 專案之[REOBJECT](/windows/win32/api/richole/ns-richole-reobject)結構的指標。 新`CRichEditCntrItem`的物件是以這個 OLE 專案為圍繞。 如果*preo*為 Null, 則用戶端專案是空的。

*pContainer*<br/>
將包含此專案之容器檔案的指標。 如果*pContainer*為 Null, 您就必須明確地呼叫[COleDocument:: AddItem](../../mfc/reference/coledocument-class.md#additem) , 將此用戶端專案加入檔中。

### <a name="remarks"></a>備註

此函式不會執行任何 OLE 初始化。

如需詳細資訊, 請參閱 Windows SDK 中的[REOBJECT](/windows/win32/api/richole/ns-richole-reobject)結構。

##  <a name="synctoricheditobject"></a>CRichEditCntrItem:: SyncToRichEditObject

呼叫此函式可將此`CRichEditCntrltem`的裝置外觀 ( [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)) 與*reo*所指定的同步處理。

```
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>參數

*reo*<br/>
參考描述 OLE 專案的[REOBJECT](/windows/win32/api/richole/ns-richole-reobject)結構。

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱 Windows SDK 中的[DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) 。

## <a name="see-also"></a>另請參閱

[MFC 範例 WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc 類別](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView 類別](../../mfc/reference/cricheditview-class.md)
