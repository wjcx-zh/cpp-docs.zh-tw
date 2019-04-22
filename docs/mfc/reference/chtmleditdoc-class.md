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
ms.openlocfilehash: c2a00b2501647f6101fed8ed1d4cd23dad7ab209
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767056"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc 類別

具有[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)，提供 WebBrowser 編輯平台在 MFC 的文件檢視架構內容中的功能。

## <a name="syntax"></a>語法

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|建構 `CHtmlEditDoc` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHtmlEditDoc::GetView](#getview)|擷取`CHtmlEditView`物件附加至這份文件。|
|[CHtmlEditDoc::IsModified](#ismodified)|傳回相關聯的檢視 WebBrowser 控制項是否包含已由使用者修改文件。|
|[CHtmlEditDoc::OpenURL](#openurl)|開啟的 URL。|

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>需求

**Header:** afxhtml.h

##  <a name="chtmleditdoc"></a>  CHtmlEditDoc::CHtmlEditDoc

建構 `CHtmlEditDoc` 物件。

```
CHtmlEditDoc();
```

##  <a name="getview"></a>  CHtmlEditDoc::GetView

擷取[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)物件附加至這份文件。

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>傳回值

讓指標回到文件的`CHtmlEditView`物件。

##  <a name="ismodified"></a>  CHtmlEditDoc::IsModified

傳回相關聯的檢視 WebBrowser 控制項是否包含已由使用者修改文件。

```
virtual BOOL IsModified();
```

##  <a name="openurl"></a>  CHtmlEditDoc::OpenURL

開啟的 URL。

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>參數

*lpszURL*<br/>
要開啟的 URL。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

## <a name="see-also"></a>另請參閱

[HTMLEdit 範例](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
