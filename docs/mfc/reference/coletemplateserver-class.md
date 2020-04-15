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
ms.openlocfilehash: ddd7a8ce70fe49e66e1175e413418fd59a89c917
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374858"
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
|[COle 範本伺服器:COleTemplate 伺服器](#coletemplateserver)|建構 `COleTemplateServer` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleTemplate 伺服器:連接樣本](#connecttemplate)|將文檔範本連接到`COleObjectFactory`基礎 物件。|
|[COleTemplate伺服器:取消註冊](#unregister)|取消註冊關聯的文檔範本。|
|[COleTemplate伺服器:更新註冊](#updateregistry)|將文件類型註冊到 OLE 系統註冊表。|

## <a name="remarks"></a>備註

此類派生自類[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md);通常,您可以直接使用`COleTemplateServer`,而不是派生您自己的類。 `COleTemplateServer`使用[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)物件管理伺服器文件。 在實現`COleTemplateServer`完整伺服器時使用,即可作為獨立應用程式運行的伺服器。 儘管支援單一文檔介面 (SDI) 應用程式,但完整伺服器通常是多個文檔介面 (MDI) 應用程式。 對於`COleTemplateServer`應用程式支援的每種類型的伺服器文檔,需要一個物件;也就是說,如果伺服器應用程式同時支援工作表和圖表,則必須有兩`COleTemplateServer`個物件。

`COleTemplateServer`覆蓋`OnCreateInstance``COleObjectFactory`由定義的成員函數。 框架調用此成員函數以創建正確類型的C++物件。

有關伺服器的詳細資訊,請參閱文章[「伺服器:實現伺服器](../../mfc/servers-implementing-a-server.md)」。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObject 工廠](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="coletemplateservercoletemplateserver"></a><a name="coletemplateserver"></a>COle 範本伺服器:COleTemplate 伺服器

建構 `COleTemplateServer` 物件。

```
COleTemplateServer();
```

### <a name="remarks"></a>備註

有關類使用方式的簡要說明,`COleTemplateServer`請參閱[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)類概述。

## <a name="coletemplateserverconnecttemplate"></a><a name="connecttemplate"></a>COleTemplate 伺服器:連接樣本

將*pDocTemplate*指向的文件範本連接到基礎的[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)物件。

```
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>參數

*Clsid*<br/>
引用範本請求的 OLE 類識別碼。

*pDocTemplate*<br/>
指向文檔範本的指標。

*b 多實體*<br/>
指示應用程式的單個實例是否可以支援多個實例。 如果為 TRUE,則為每個請求啟動應用程式的多個實例以創建物件。

### <a name="remarks"></a>備註

關於詳細資訊,請參閱 Windows SDK 中的[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)。

## <a name="coletemplateserverunregister"></a><a name="unregister"></a>COleTemplate伺服器:取消註冊

取消註冊關聯的文檔範本。

```
BOOL Unregister();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

輸入註解

## <a name="coletemplateserverupdateregistry"></a><a name="updateregistry"></a>COleTemplate伺服器:更新註冊

從文件範本字串載入檔類型資訊,並將該資訊放在 OLE 系統註冊表中。

```
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>參數

*nAppType*<br/>
OLE_APPTYPE枚舉中的值,在 AFXDISP 中定義。H。 它可以具有以下任一值:

- OAT_INPLACE_SERVER伺服器具有完整的伺服器用戶介面。

- OAT_SERVER伺服器僅支援嵌入。

- OAT_CONTAINER容器支援指向嵌入物件的連結。

- OAT_DISPATCH_OBJECT`IDispatch`物件 是 - 支援。

- OAT_DOC_OBJECT_SERVER伺服器支援嵌入和文檔物件元件模型。

*rglpsz註冊*<br/>
僅當不存在項目時,才寫入註冊表的條目的清單。

*rglpsz 覆寫*<br/>
寫入註冊表的條目清單,而不考慮是否存在任何前面的條目。

*b 註冊*<br/>
確定是否應註冊類。 如果*b寄存器*為 TRUE,則類將註冊到系統註冊表。 否則,它將取消註冊類。

### <a name="remarks"></a>備註

註冊資訊透過呼叫[CDocTemplate 載入:GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 檢索的子字串是索引標識的子字`regFileTypeId`串,`regFileTypeName`和`fileNewName`,如`GetDocString`參考頁中所述。

如果`regFileTypeId`子字串為空,或者調用`GetDocString`失敗的原因為任何其他原因,則此函數將失敗,並且未在註冊表中輸入檔資訊。

參數*rglpsz 註冊*和*rglpszOverwrite*中的資訊通過調用[AfxOleRegisterServerServerClass](application-control.md#afxoleregisterserverclass)寫入註冊表。 默認資訊在兩個參數為 NULL 時註冊,適用於大多數應用程式。 有關這些參數中資訊的結構的資訊,請參`AfxOleRegisterServerClass`閱 。

如需詳細資訊，請參閱 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

## <a name="see-also"></a>另請參閱

[MFC 樣品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory 類別](../../mfc/reference/coleobjectfactory-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)
