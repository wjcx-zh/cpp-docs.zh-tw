---
title: CMultiPageDHtmlDialog 類別
ms.date: 11/04/2016
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
ms.openlocfilehash: 66ab996a810c7409d689d600758828130d4237f1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283744"
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
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|建構多頁的 （精靈式） DHTML 對話方塊物件。|
|[CMultiPageDHtmlDialog::~CMultiPageDHtmlDialog](#cmultipagedhtmldialog__~cmultipagedhtmldialog)|終結多頁 DHTML 對話方塊物件。|

## <a name="remarks"></a>備註

執行此動作的機制是[DHTML 和 URL 事件對應](dhtml-event-maps.md)，其中包含內嵌事件對應每個頁面。

## <a name="example"></a>範例

此多頁對話方塊假設定義簡單的精靈式功能的三個 HTML 資源。 第一頁已**下一步**  按鈕，第二**Prev**並**下一步**按鈕，然後第三個**Prev**  按鈕。 按下其中一個按鈕時，處理常式函式會呼叫[CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource)載入適當的新頁面。

類別中的宣告 （CMyMultiPageDlg.h) 關聯的部分：

[!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]

類別中的實作 （CMyMultipageDlg.cpp) 關聯的部分：

[!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

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

**標頭：** afxdhtml.h

##  <a name="cmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog::CMultiPageDHtmlDialog

建構多頁的 （精靈式） DHTML 對話方塊物件。

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

*lpszTemplateName*<br/>
以 null 結尾的字串，這是對話方塊範本資源的名稱。

*szHtmlResID*<br/>
以 null 結尾字串的 HTML 資源的名稱。

*pParentWnd*<br/>
父系或擁有者的視窗物件的指標 (型別的[CWnd](../../mfc/reference/cwnd-class.md)) 所屬之對話方塊物件。 如果它是 NULL 時，對話方塊物件的父視窗設為主要的應用程式視窗。

*nIDTemplate*<br/>
包含對話方塊範本資源的識別碼。

*nHtmlResID*<br/>
包含的 HTML 資源的識別碼。

##  <a name="_dtorcmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog

終結多頁 DHTML 對話方塊物件。

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>另請參閱

[CDHtmlDialog 類別](../../mfc/reference/cdhtmldialog-class.md)
