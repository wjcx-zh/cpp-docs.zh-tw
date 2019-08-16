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
ms.openlocfilehash: 4a1997497f3bddb405b712b5534f76e577dabfa8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503086"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer 類別

用於 OLE 視覺化編輯伺服程式、Automation 伺服程式和連結容器 (支援內嵌連結的應用程式)。

## <a name="syntax"></a>語法

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|建構 `COleTemplateServer` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|將檔範本連接到基礎`COleObjectFactory`物件。|
|[COleTemplateServer::Unregister](#unregister)|取消註冊相關聯的檔範本。|
|[COleTemplateServer::UpdateRegistry](#updateregistry)|向 OLE 系統登錄註冊檔案類型。|

## <a name="remarks"></a>備註

這個類別衍生自類別[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md);通常, 您可以直接`COleTemplateServer`使用, 而不是衍生您自己的類別。 `COleTemplateServer`使用[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)物件來管理伺服器檔。 在`COleTemplateServer`執行完整伺服器 (也就是可當做獨立應用程式執行的伺服器) 時使用。 完整伺服器通常是多個檔介面 (MDI) 應用程式, 不過支援單一檔介面 (SDI) 應用程式。 應用`COleTemplateServer`程式支援的每個伺服器檔案類型都需要一個物件; 也就是說, 如果您的伺服器應用程式同時支援工作表和圖表, 則您`COleTemplateServer`必須有兩個物件。

`COleTemplateServer`覆寫`OnCreateInstance`由`COleObjectFactory`定義的成員函式。 此成員函式會由架構呼叫, 以建立C++適當類型的物件。

如需伺服器的詳細資訊, 請參閱[伺服器:執行伺服器](../../mfc/servers-implementing-a-server.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="coletemplateserver"></a>COleTemplateServer:: COleTemplateServer

建構 `COleTemplateServer` 物件。

```
COleTemplateServer();
```

### <a name="remarks"></a>備註

如需使用`COleTemplateServer`類別的簡短描述, 請參閱[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)類別總覽。

##  <a name="connecttemplate"></a>  COleTemplateServer::ConnectTemplate

將*pDocTemplate*所指向的檔範本連接到基礎[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)物件。

```
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>參數

*clsid*<br/>
範本要求之 OLE 類別 ID 的參考。

*pDocTemplate*<br/>
檔範本的指標。

*bMultiInstance*<br/>
指出應用程式的單一實例是否可以支援多個具現化。 若為 TRUE, 則會針對每個建立物件的要求啟動應用程式的多個實例。

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱 Windows SDK 中的[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)。

##  <a name="unregister"></a>  COleTemplateServer::Unregister

取消註冊相關聯的檔範本。

```
BOOL Unregister();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

EnterRemarks

##  <a name="updateregistry"></a>COleTemplateServer:: UpdateRegistry

從檔範本字串載入檔案類型資訊, 並將該資訊放在 OLE 系統登錄中。

```
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>參數

*nAppType*<br/>
來自 OLE_APPTYPE 列舉的值, 其定義于 AFXDISP.H 中。H. 它可以具有下列任何一個值:

- OAT_INPLACE_SERVER 伺服器具有完整的伺服器使用者介面。

- OAT_SERVER 伺服器僅支援內嵌。

- OAT_CONTAINER 容器支援内嵌物件的連結。

- OAT_DISPATCH_OBJECT 物件是`IDispatch`可支援的。

- OAT_DOC_OBJECT_SERVER 伺服器支援內嵌和檔物件元件模型。

*rglpszRegister*<br/>
只有在沒有專案存在時, 才會寫入登錄中的專案清單。

*rglpszOverwrite*<br/>
寫入登錄中的專案清單, 不論任何先前的專案是否存在。

*bRegister*<br/>
判斷是否要註冊類別。 如果*bRegister*為 TRUE, 則會向系統登錄註冊類別。 否則, 它會取消註冊類別。

### <a name="remarks"></a>備註

註冊資訊是藉由呼叫[CDocTemplate:: GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)來載入。 所抓取的子字串是由`regFileTypeId`索引、 `regFileTypeName`和`fileNewName`所識別, 如`GetDocString`參考頁面所述。

如果子`regFileTypeId`字串是空的, 或`GetDocString`呼叫因任何其他原因而失敗, 則此函式會失敗, 且不會在登錄中輸入檔案資訊。

引數*rglpszRegister*和*rglpszOverwrite*中的資訊會透過對[AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass)的呼叫寫入登錄。 當兩個引數都是 Null 時, 所註冊的預設資訊適用于大部分的應用程式。 如需這些引數中資訊結構的詳細資訊, 請`AfxOleRegisterServerClass`參閱。

如需詳細資訊，請參閱 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory 類別](../../mfc/reference/coleobjectfactory-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)
