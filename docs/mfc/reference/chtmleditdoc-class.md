---
title: CHtmlEditDoc 類別
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditDoc
- AFXHTML/CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::GetView
- AFXHTML/CHtmlEditDoc::IsModified
- AFXHTML/CHtmlEditDoc::OpenURL
helpviewer_keywords:
- CHtmlEditDoc [MFC], CHtmlEditDoc
- CHtmlEditDoc [MFC], GetView
- CHtmlEditDoc [MFC], IsModified
- CHtmlEditDoc [MFC], OpenURL
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
ms.openlocfilehash: 8b500f651da1a73040fdb0469f2f023babe25e85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352166"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc 類別

使用[CHtmlEditView](../../mfc/reference/chtmleditview-class.md),在 MFC 文件檢視架構結構的上下文中提供 Web 瀏覽器編輯平臺的功能。

## <a name="syntax"></a>語法

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHtml 編輯檔:CHtml編輯多克](#chtmleditdoc)|建構 `CHtmlEditDoc` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHtml 編輯檔案:取得檢視](#getview)|檢索附加到此`CHtmlEditView`文件的物件。|
|[CHtmlEditDoc:已修改](#ismodified)|返回關聯的檢視的 WebBrowser 控制件是否包含使用者已修改的文檔。|
|[CHtml編輯檔::開啟 URL](#openurl)|打開 URL。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>需求

**Header:** afxhtml.h

## <a name="chtmleditdocchtmleditdoc"></a><a name="chtmleditdoc"></a>CHtml 編輯檔:CHtml編輯多克

建構 `CHtmlEditDoc` 物件。

```
CHtmlEditDoc();
```

## <a name="chtmleditdocgetview"></a><a name="getview"></a>CHtml 編輯檔案:取得檢視

檢索附加到本文檔的[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)物件。

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>傳回值

返回指向文件`CHtmlEditView`物件的指標。

## <a name="chtmleditdocismodified"></a><a name="ismodified"></a>CHtmlEditDoc:已修改

返回關聯的檢視的 WebBrowser 控制件是否包含使用者已修改的文檔。

```
virtual BOOL IsModified();
```

## <a name="chtmleditdocopenurl"></a><a name="openurl"></a>CHtml編輯檔::開啟 URL

打開 URL。

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>參數

*lpszURL*<br/>
要開啟的 URL。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="see-also"></a>另請參閱

[HTML編輯範例](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
