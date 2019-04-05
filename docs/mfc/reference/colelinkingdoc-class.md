---
title: COleLinkingDoc 類別
ms.date: 11/04/2016
f1_keywords:
- COleLinkingDoc
- AFXOLE/COleLinkingDoc
- AFXOLE/COleLinkingDoc::COleLinkingDoc
- AFXOLE/COleLinkingDoc::Register
- AFXOLE/COleLinkingDoc::Revoke
- AFXOLE/COleLinkingDoc::OnFindEmbeddedItem
- AFXOLE/COleLinkingDoc::OnGetLinkedItem
helpviewer_keywords:
- COleLinkingDoc [MFC], COleLinkingDoc
- COleLinkingDoc [MFC], Register
- COleLinkingDoc [MFC], Revoke
- COleLinkingDoc [MFC], OnFindEmbeddedItem
- COleLinkingDoc [MFC], OnGetLinkedItem
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
ms.openlocfilehash: c5076ceef0c6626fac0232fadf6818edd78b4ccf
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58773550"
---
# <a name="colelinkingdoc-class"></a>COleLinkingDoc 類別

支援連結至所包含內嵌項目之 OLE 容器文件的基底類別。

## <a name="syntax"></a>語法

```
class COleLinkingDoc : public COleDocument
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|建構 `COleLinkingDoc` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleLinkingDoc::Register](#register)|向 OLE 系統 Dll 中的文件。|
|[COleLinkingDoc::Revoke](#revoke)|撤銷文件的註冊。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|尋找指定的內嵌項目。|
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|尋找指定的連結項目。|

## <a name="remarks"></a>備註

支援內嵌的項目連結的容器應用程式稱為 「 連結容器 」。 [OCLIENT](../../overview/visual-cpp-samples.md)範例應用程式是連結的容器的範例。

連結項目來源時，包含文件必須載入編輯內嵌項目順序中的其他文件中內嵌項目。 基於這個理由，連結的容器必須要能夠啟動另一個容器應用程式，當使用者想要編輯連結的項目來源。 您的應用程式也必須使用[COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)類別，使它可以建立文件時以程式設計方式啟動。

若要讓您的容器連結的容器，衍生您的文件類別，從`COleLinkingDoc`而非[COleDocument](../../mfc/reference/coledocument-class.md)。 如同其他任何 OLE 容器，您必須設計您的類別來儲存應用程式的原生資料，以及內嵌或連結的項目。 此外，您必須設計來儲存您的原生資料的資料結構。 如果您定義`CDocItem`-衍生類別，您的應用程式的原生資料，您可以使用所定義的介面`COleDocument`來儲存您的原生資料，以及您 OLE 的資料。

若要允許另一個容器來以程式設計方式啟動您的應用程式，請宣告`COleTemplateServer`物件做為您的應用程式的成員`CWinApp`-衍生的類別：

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

在 `InitInstance`成員函式您`CWinApp`-衍生的類別，建立文件範本，並指定您`COleLinkingDoc`-衍生類別，當做文件類別：

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

連接您`COleTemplateServer`藉由呼叫物件的文件範本的物件`ConnectTemplate`成員函式，並藉由呼叫物件在 OLE 系統的所有類別的註冊`COleTemplateServer::RegisterAll`:

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

如需相關範例`CWinApp`-衍生類別定義和`InitInstance`函式中，請參閱 OCLIENT。H 和 OCLIENT。MFC 範例中的 CPP [OCLIENT](../../overview/visual-cpp-samples.md)。

如需有關使用`COleLinkingDoc`，請參閱文章[容器：實作容器](../../mfc/containers-implementing-a-container.md)和[容器：進階功能](../../mfc/containers-advanced-features.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>需求

**標頭：** afxole.h

##  <a name="colelinkingdoc"></a>  COleLinkingDoc::COleLinkingDoc

建構`COleLinkingDoc`沒有開始與 OLE 系統 Dll 的通訊物件。

```
COleLinkingDoc();
```

### <a name="remarks"></a>備註

您必須呼叫`Register`成員函式，以通知 OLE 文件已開啟。

##  <a name="onfindembeddeditem"></a>  COleLinkingDoc::OnFindEmbeddedItem

由架構呼叫以判斷文件是否包含具有指定名稱的內嵌的 OLE 項目。

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>參數

*lpszItemName*<br/>
內嵌 OLE 項目要求的名稱的指標。

### <a name="return-value"></a>傳回值

指定的項目; 指標如果找不到項目，則為 NULL。

### <a name="remarks"></a>備註

預設實作會搜尋具有指定名稱 （名稱比較不區分大小寫的） 項目的內嵌項目清單。 如果您有自己的方法，來儲存或命名內嵌的 OLE 項目，請覆寫這個函式。

##  <a name="ongetlinkeditem"></a>  COleLinkingDoc::OnGetLinkedItem

由架構呼叫以檢查文件是否包含具有指定名稱的連結的伺服器項目。

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>參數

*lpszItemName*<br/>
指標的項目要求的 OLE 連結名稱。

### <a name="return-value"></a>傳回值

指定的項目; 指標如果找不到項目，則為 NULL。

### <a name="remarks"></a>備註

預設值`COleLinkingDoc`實作一定會傳回 NULL。 此函式是在衍生類別中的覆寫`COleServerDoc`来搜尋的連結的項目具有指定名稱 （名稱比較是區分大小寫） 的 OLE 伺服器項目清單。 如果您已實作您自己的方法，來儲存或擷取連結的伺服器項目，請覆寫這個函式。

##  <a name="register"></a>  COleLinkingDoc::Register

通知 OLE 系統 Dll 已開啟的文件。

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>參數

*pFactory*<br/>
（可以是 NULL） 的 OLE factory 物件的指標。

*lpszPathName*<br/>
容器文件的完整路徑的指標。

### <a name="return-value"></a>傳回值

非零值，如果已成功註冊文件;否則為 0。

### <a name="remarks"></a>備註

呼叫此函式時建立或開啟文件向 OLE 系統 Dll 命名的檔案。 沒有需要呼叫此函式，如果文件表示內嵌的項目。

如果您使用`COleTemplateServer`在您的應用程式`Register`會為您呼叫`COleLinkingDoc`的實作`OnNewDocument`， `OnOpenDocument`，和`OnSaveDocument`。

##  <a name="revoke"></a>  COleLinkingDoc::Revoke

文件已不再開放通知 OLE 系統 Dll。

```
void Revoke();
```

### <a name="remarks"></a>備註

呼叫此函式來撤銷文件的註冊與 OLE 系統 Dll。

具名的檔案，在關閉時，您應該呼叫此函式，但您通常不必直接呼叫它。 `Revoke` 針對您藉由呼叫`COleLinkingDoc`的實作`OnCloseDocument`， `OnNewDocument`， `OnOpenDocument`，和`OnSaveDocument`。

## <a name="see-also"></a>另請參閱

[MFC 範例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDocument 類別](../../mfc/reference/coledocument-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)
