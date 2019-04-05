---
title: COleTemplateServer 類別
ms.date: 11/04/2016
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
ms.openlocfilehash: 3abdf1dc2da5ef9a111371b501d5cd8ce208825d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781207"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer 類別

用於 OLE 視覺化編輯伺服程式、Automation 伺服程式和連結容器 (支援內嵌連結的應用程式)。

## <a name="syntax"></a>語法

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|建構 `COleTemplateServer` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|連接至基礎的文件範本`COleObjectFactory`物件。|
|[COleTemplateServer::Unregister](#unregister)|取消註冊的相關聯的文件範本。|
|[COleTemplateServer::UpdateRegistry](#updateregistry)|使用 OLE 系統登錄中註冊的文件類型。|

## <a name="remarks"></a>備註

這個類別衍生自類別[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); 通常，您可以使用`COleTemplateServer`直接而不是衍生您自己的類別。 `COleTemplateServer` 會使用[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)物件來管理伺服器文件。 使用`COleTemplateServer`實作完整的伺服器，也就是可以當作獨立的應用程式執行的伺服器時。 完整的伺服器通常是多個文件介面 (MDI) 應用程式，雖然支援單一文件介面 (SDI) 應用程式。 一`COleTemplateServer`所需應用程式支援的伺服器文件的每個類型的物件; 也就是說，如果您的伺服器應用程式支援的工作表和圖表，您必須有兩個`COleTemplateServer`物件。

`COleTemplateServer` 覆寫`OnCreateInstance`所定義的成員函式`COleObjectFactory`。 此成員函式是由建立適當類型的 c + + 物件架構呼叫。

如需有關伺服器的詳細資訊，請參閱[伺服器：實作伺服器](../../mfc/servers-implementing-a-server.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="coletemplateserver"></a>  COleTemplateServer::COleTemplateServer

建構 `COleTemplateServer` 物件。

```
COleTemplateServer();
```

### <a name="remarks"></a>備註

如需簡短的使用說明`COleTemplateServer`類別，請參閱[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)類別概觀。

##  <a name="connecttemplate"></a>  COleTemplateServer::ConnectTemplate

連接所指的文件範本*pDocTemplate*基礎[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)物件。

```
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>參數

*clsid*<br/>
參考範本要求的 OLE 類別識別碼。

*pDocTemplate*<br/>
文件範本的指標。

*bMultiInstance*<br/>
指出應用程式的單一執行個體是否可以支援多個具現化。 如果為 TRUE，針對每個要求建立物件啟動應用程式的多個執行個體。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [CLSID 金鑰](/windows/desktop/com/clsid-key-hklm)Windows SDK 中。

##  <a name="unregister"></a>  COleTemplateServer::Unregister

取消註冊的相關聯的文件範本。

```
BOOL Unregister();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

EnterRemarks

##  <a name="updateregistry"></a>  COleTemplateServer::UpdateRegistry

檔案型別資訊從載入的文件樣板字串，並將該資訊放在 OLE 系統登錄中。

```
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>參數

*nAppType*<br/>
從定義於 AFXDISP OLE_APPTYPE 列舉的值。H. 它可以包含下列值之一：

- OAT_INPLACE_SERVER 伺服器具有完整伺服器的使用者介面。

- OAT_SERVER 伺服器支援僅內嵌。

- OAT_CONTAINER 容器支援內嵌物件連結。

- OAT_DISPATCH_OBJECT 物件是`IDispatch`-支援。

- OAT_DOC_OBJECT_SERVER 伺服器同時支援內嵌和文件物件元件模型。

*rglpszRegister*<br/>
只有當沒有任何項目存在，會寫入登錄的項目清單。

*rglpszOverwrite*<br/>
寫入到登錄中，不論任何上述項目是否存在的項目清單。

*bRegister*<br/>
判斷類別是否註冊。 如果*bRegister*為 TRUE 時，此類別向系統登錄。 否則，它會取消註冊類別。

### <a name="remarks"></a>備註

註冊資訊會透過呼叫載入[CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 擷取子字串是索引所識別出那些`regFileTypeId`， `regFileTypeName`，並`fileNewName`所述，在`GetDocString`參考頁面。

如果`regFileTypeId`是空的子字串或是呼叫`GetDocString`失敗的任何其他原因，此函式失敗，而且未在登錄中輸入的檔案資訊。

引數中的資訊*rglpszRegister*並*rglpszOverwrite*透過呼叫登錄寫入[AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass)。 預設資訊，註冊之後，當兩個引數都是 NULL 時，適合大部分的應用程式。 如需這些引數中的資訊結構的資訊，請參閱`AfxOleRegisterServerClass`。

如需詳細資訊，請參閱 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory 類別](../../mfc/reference/coleobjectfactory-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)
