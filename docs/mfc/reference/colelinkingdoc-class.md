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
ms.openlocfilehash: 1fad986b7e7304075cacb0b5ced9feeb8af4664f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753847"
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
|[COle 連結文件::COle連結文件](#colelinkingdoc)|建構 `COleLinkingDoc` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COle 連結文件::註冊](#register)|將文件註冊到 OLE 系統 DLL。|
|[COle 連結文件:撤銷](#revoke)|撤銷文檔的註冊。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[COle 連結文件::在尋找嵌入式項目](#onfindembeddeditem)|尋找指定的嵌入項。|
|[COlelinkDoc::上鏈接專案](#ongetlinkeditem)|尋找指定的連結項。|

## <a name="remarks"></a>備註

支援連結到嵌入項的容器應用程式稱為"連結容器」。 [OCLIENT](../../overview/visual-cpp-samples.md)範例應用程式是連結容器的範例。

當連結項的源是另一個文檔中的嵌入項時,必須載入包含文檔才能編輯嵌入項。 因此,當使用者想要編輯連結項的源時,連結容器必須能夠由另一個容器應用程式啟動。 您的應用程式還必須使用[COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)類,以便在以程式設計方式啟動時創建文檔。

要使容器成為連結容器,請從`COleLinkingDoc`[COleDocument](../../mfc/reference/coledocument-class.md)派生文檔類。 與任何其他 OLE 容器一樣,必須設計用於儲存應用程式的本機數據以及嵌入或連結項的類。 此外,還必須設計用於存儲本機數據的數據結構。 如果為應用程式的本機`CDocItem`數據定義派生類,則可以使用`COleDocument`定義的 介面來存儲本機數據和 OLE 資料。

要允許應用程式由另一個容器以程式設計方式啟動,請聲明`COleTemplateServer`物件為`CWinApp`應用程式 派生類的成員:

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

在`InitInstance``CWinApp`派生類別的成員函數中,建立文件樣本並將`COleLinkingDoc`派生類指定為文件類:

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

以呼叫`COleTemplateServer``ConnectTemplate`物件的成員函數會連接到文件樣本,並透過呼叫`COleTemplateServer::RegisterAll`:

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

有關範例`CWinApp`派生類定義`InitInstance`和函數,請參閱 OCLIENT。H 和 OCLIENT。MFC 樣本[OCLIENT](../../overview/visual-cpp-samples.md)中的 CPP。

有關使用`COleLinkingDoc`的詳細資訊,請參閱[文章容器:實現容器](../../mfc/containers-implementing-a-container.md)和[容器:進階功能](../../mfc/containers-advanced-features.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="colelinkingdoccolelinkingdoc"></a><a name="colelinkingdoc"></a>COle 連結文件::COle連結文件

建構`COleLinkingDoc`物件而不開始與 OLE 系統 DLL 通訊。

```
COleLinkingDoc();
```

### <a name="remarks"></a>備註

您必須調用`Register`成員函數,通知 OLE 文件已打開。

## <a name="colelinkingdoconfindembeddeditem"></a><a name="onfindembeddeditem"></a>COle 連結文件::在尋找嵌入式項目

由框架呼叫以確定文件是否包含具有指定名稱的嵌入式 OLE 項。

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>參數

*lpszItem名稱*<br/>
指向請求的嵌入 OLE 項的名稱。

### <a name="return-value"></a>傳回值

指向指定項的指標;指向指定項的指標。如果未找到該專案,則為 NULL。

### <a name="remarks"></a>備註

默認實現搜索具有指定名稱的項的嵌入項列表(名稱比較區分大小寫)。 如果您有自己的方法來儲存或命名嵌入的 OLE 項,請重寫此函數。

## <a name="colelinkingdocongetlinkeditem"></a><a name="ongetlinkeditem"></a>COlelinkDoc::上鏈接專案

由框架呼叫以檢查文件是否包含具有指定名稱的連結伺服器項。

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>參數

*lpszItem名稱*<br/>
指向請求的連結 OLE 項的名稱。

### <a name="return-value"></a>傳回值

指向指定項的指標;指向指定項的指標。如果未找到該專案,則為 NULL。

### <a name="remarks"></a>備註

預設`COleLinkingDoc`實現始終返回 NULL。 此函數在派生類`COleServerDoc`中重寫,以搜索具有指定名稱的連結項的 OLE 伺服器項列表(名稱比較區分大小寫)。 如果您已經實現了自己的存儲或檢索連結的伺服器項的方法,請重寫此函數。

## <a name="colelinkingdocregister"></a><a name="register"></a>COle 連結文件::註冊

通知 OLE 系統 DLL 文件已打開。

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>參數

*pFactory*<br/>
指向 OLE 工廠物件的指標(可以是 NULL)。

*lpszPath名稱*<br/>
指向容器文件完全限定路徑的指標。

### <a name="return-value"></a>傳回值

如果文檔已成功註冊,則非零;否則 0。

### <a name="remarks"></a>備註

建立或打開命名檔案以將文件註冊到 OLE 系統 DLL 時調用此功能。 如果文檔表示嵌入的項,則無需調用此函數。

如果在應用程式中使用`COleTemplateServer``Register`,`COleLinkingDoc`則由`OnNewDocument`的執行`OnSaveDocument``OnOpenDocument`。

## <a name="colelinkingdocrevoke"></a><a name="revoke"></a>COle 連結文件:撤銷

通知 OLE 系統 DLL 文件不再打開。

```cpp
void Revoke();
```

### <a name="remarks"></a>備註

呼叫此函數以撤銷文件在 OLE 系統 DLL 中的註冊。

關閉命名檔時應調用此函數,但通常不需要直接調用它。 `Revoke`是`COleLinkingDoc`按`OnCloseDocument`的實作來呼`OnNewDocument`叫`OnOpenDocument`的`OnSaveDocument`, 與 。

## <a name="see-also"></a>另請參閱

[MFC 樣品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDocument 類別](../../mfc/reference/coledocument-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)
