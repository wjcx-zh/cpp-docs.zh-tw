---
title: CMultiPageDHtmlDialog 類別
ms.date: 03/27/2019
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
ms.openlocfilehash: 89e4830c3b5c6cb663ca2d2935adaaae3f356958
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319657"
---
# <a name="cmultipagedhtmldialog-class"></a>CMultiPageDHtmlDialog 類別

多頁對話方塊會循序顯示多個 HTML 網頁並處理來自每頁的事件。

## <a name="syntax"></a>語法

```
class CMultiPageDHtmlDialog : public CDHtmlDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 多頁Html對話::C多頁DHtml對話](#cmultipagedhtmldialog)|建構多頁(嚮導樣式)DHTML對話框物件。|
|[C 多頁Html對話::_c多頁DHtml對話](#_dtorcmultipagedhtmldialog)|銷毀多頁 DHTML 對話框物件。|

## <a name="remarks"></a>備註

執行此操作的機制是[DHTML 和 URL 事件映射](dhtml-event-maps.md),其中包含每個頁面的嵌入事件映射。

## <a name="example"></a>範例

此多頁對話框假定三個 HTML 資源定義類似於精靈的簡單功能。 第一頁有一個 **「下一步**」按鈕,第二個按鈕為 **「Prev」** 和 **「下一步**」按鈕,第三頁具有 **「Prev」** 按鈕。 按下其中一個按鈕時,處理程式函數將調用[CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource)以載入相應的新頁面。

類聲明的相關部分(在 CMyMultiPageDlg.h 中):

[!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]

類別實現的相關部分(在 CMyMultipageDlg.cpp 中):

[!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)

`CMultiPageDHtmlDialog`

## <a name="requirements"></a>需求

**標題:** afxdhtml.h

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="cmultipagedhtmldialog"></a>C 多頁Html對話::C多頁DHtml對話

建構多頁(嚮導樣式)DHTML對話框物件。

```
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID = NULL,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog();
```

### <a name="parameters"></a>參數

*lpszTemplate 名稱*<br/>
為對話框樣本資源名稱的 null 終止字串。

*什奇雷斯ID*<br/>
為 HTML 資源名稱的 null 終止字串。

*pparentwnd*<br/>
指向對話框物件所屬的父視窗或所有者視窗物件的指標[(CWnd](../../mfc/reference/cwnd-class.md)類型)。 如果為 NULL,則對話方塊物件的父視窗將設置為主應用程式視窗。

*nIDTemplate*<br/>
包含對話方塊樣本資源的 ID 號。

*nHtmlResID*<br/>
包含 HTML 資源的 ID 號。

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="_dtorcmultipagedhtmldialog"></a>C 多頁Html對話::_c多頁DHtml對話

銷毀多頁 DHTML 對話框物件。

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>另請參閱

[CDHtmlDialog 類別](../../mfc/reference/cdhtmldialog-class.md)
