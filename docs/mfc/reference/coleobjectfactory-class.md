---
title: COleObjectFactory 類別
ms.date: 11/04/2016
f1_keywords:
- COleObjectFactory
- AFXDISP/COleObjectFactory
- AFXDISP/COleObjectFactory::COleObjectFactory
- AFXDISP/COleObjectFactory::GetClassID
- AFXDISP/COleObjectFactory::IsLicenseValid
- AFXDISP/COleObjectFactory::IsRegistered
- AFXDISP/COleObjectFactory::Register
- AFXDISP/COleObjectFactory::RegisterAll
- AFXDISP/COleObjectFactory::Revoke
- AFXDISP/COleObjectFactory::RevokeAll
- AFXDISP/COleObjectFactory::UnregisterAll
- AFXDISP/COleObjectFactory::UpdateRegistry
- AFXDISP/COleObjectFactory::UpdateRegistryAll
- AFXDISP/COleObjectFactory::GetLicenseKey
- AFXDISP/COleObjectFactory::OnCreateObject
- AFXDISP/COleObjectFactory::VerifyLicenseKey
- AFXDISP/COleObjectFactory::VerifyUserLicense
helpviewer_keywords:
- COleObjectFactory [MFC], COleObjectFactory
- COleObjectFactory [MFC], GetClassID
- COleObjectFactory [MFC], IsLicenseValid
- COleObjectFactory [MFC], IsRegistered
- COleObjectFactory [MFC], Register
- COleObjectFactory [MFC], RegisterAll
- COleObjectFactory [MFC], Revoke
- COleObjectFactory [MFC], RevokeAll
- COleObjectFactory [MFC], UnregisterAll
- COleObjectFactory [MFC], UpdateRegistry
- COleObjectFactory [MFC], UpdateRegistryAll
- COleObjectFactory [MFC], GetLicenseKey
- COleObjectFactory [MFC], OnCreateObject
- COleObjectFactory [MFC], VerifyLicenseKey
- COleObjectFactory [MFC], VerifyUserLicense
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
ms.openlocfilehash: 22805550d13ecb400b151495363e5eda2dfb3b76
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856972"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory 類別

實作建立 OLE 物件 (例如伺服器、Automation 物件和文件) 的 OLE Class Factory。

## <a name="syntax"></a>語法

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleObjectFactory：： COleObjectFactory](#coleobjectfactory)|建構 `COleObjectFactory` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleObjectFactory：： GetClassID](#getclassid)|傳回此 factory 所建立物件的 OLE 類別 ID。|
|[COleObjectFactory：： IsLicenseValid](#islicensevalid)|判斷控制項的授權是否有效。|
|[COleObjectFactory：： IsRegistered](#isregistered)|指出物件 factory 是否已向 OLE 系統 Dll 註冊。|
|[COleObjectFactory：： Register](#register)|向 OLE 系統 Dll 註冊此物件 factory。|
|[COleObjectFactory：： RegisterAll](#registerall)|向 OLE 系統 Dll 註冊所有應用程式的物件 factory。|
|[COleObjectFactory：： Revoke](#revoke)|撤銷這個物件處理站使用 OLE 系統 Dll 的註冊。|
|[COleObjectFactory：： RevokeAll](#revokeall)|使用 OLE 系統 Dll 撤銷應用程式的物件工廠註冊。|
|[COleObjectFactory：： UnregisterAll](#unregisterall)|取消註冊應用程式的所有物件 factory。|
|[COleObjectFactory：： UpdateRegistry](#updateregistry)|向 OLE 系統登錄註冊此物件 factory。|
|[COleObjectFactory：： UpdateRegistryAll](#updateregistryall)|向 OLE 系統登錄註冊所有應用程式的物件 factory。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[COleObjectFactory：： GetLicenseKey](#getlicensekey)|向控制項的 DLL 要求唯一索引鍵。|
|[COleObjectFactory：： OnCreateObject](#oncreateobject)|由架構呼叫，以建立此 factory 類型的新物件。|
|[COleObjectFactory：： VerifyLicenseKey](#verifylicensekey)|確認內嵌在控制項中的索引鍵符合容器中內嵌的索引鍵。|
|[COleObjectFactory：： VerifyUserLicense](#verifyuserlicense)|確認控制項已獲得設計階段使用的授權。|

## <a name="remarks"></a>備註

`COleObjectFactory` 類別具有執行下列功能的成員函式：

- 管理物件的註冊。

- 更新 OLE 系統暫存器，以及通知 OLE 該物件正在執行且準備好接收訊息的執行時間註冊。

- 強制執行授權，方法是在設計階段將控制項限制為授權的開發人員，並在執行時間時使用授權的應用程式。

- 向 OLE 系統登錄註冊控制物件 factory。

如需建立物件的詳細資訊，請參閱[資料物件和資料來源（OLE）](../../mfc/data-objects-and-data-sources-ole.md)和[資料物件和資料來源：建立和](../../mfc/data-objects-and-data-sources-creation-and-destruction.md)終結的文章。 如需註冊的詳細資訊，請參閱[註冊](../../mfc/registration.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="coleobjectfactory"></a>COleObjectFactory：： COleObjectFactory

建立 `COleObjectFactory` 物件、將它初始化為未註冊的物件 factory，並將它新增至 factory 清單。

```
COleObjectFactory(
    REFCLSID clsid,
    CRuntimeClass* pRuntimeClass,
    BOOL bMultiInstance,
    LPCTSTR lpszProgID);

COleObjectFactory(
    REFCLSID clsid,
    CRuntimeClass* pRuntimeClass,
    BOOL bMultiInstance,
    int nFlags,
    LPCTSTR lpszProgID);
```

### <a name="parameters"></a>參數

*clsid*<br/>
參考此物件 factory 所代表的 OLE 類別 ID。

*pRuntimeClass*<br/>
這個 factory 可以建立之C++物件的執行時間類別的指標。

*bMultiInstance*<br/>
指出應用程式的單一實例是否可以支援多個具現化。 若為 TRUE，則會針對每個建立物件的要求啟動應用程式的多個實例。

*nFlags*<br/>
包含下列一個或多個旗標：

- `afxRegDefault` 將執行緒模型設定為 ThreadingModel = 公寓。

- `afxRegInsertable` 可讓控制項出現在 OLE 物件的 [**插入物件**] 對話方塊中。

- `afxRegApartmentThreading` 將登錄中的執行緒模型設定為 ThreadingModel = 公寓。

- `afxRegFreeThreading` 將登錄中的執行緒模型設定為 ThreadingModel = Free。

   您可以將這兩個旗標 `afxRegApartmentThreading` 和 `afxRegFreeThreading` 結合，以設定 ThreadingModel = 兩者。 如需執行緒模型註冊的詳細資訊，請參閱 Windows SDK 中的[InprocServer32](/windows/win32/com/inprocserver32) 。

*lpszProgID*<br/>
包含口頭程式識別碼之字串的指標，例如 "Microsoft Excel"。

### <a name="remarks"></a>備註

不過，若要使用物件，您必須註冊它。

如需詳細資訊，請參閱 Windows SDK 中的[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)。

##  <a name="getclassid"></a>COleObjectFactory：： GetClassID

傳回此 factory 所代表之 OLE 類別 ID 的參考。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>傳回值

此 factory 所代表之 OLE 類別 ID 的參考。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)。

##  <a name="getlicensekey"></a>COleObjectFactory：： GetLicenseKey

向控制項的 DLL 要求唯一的授權金鑰，並將它儲存在*pbstrKey*所指向的 BSTR 中。

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>參數

*dwReserved*<br/>
保留供未來使用。

*pbstrKey*<br/>
將儲存授權金鑰之 BSTR 的指標。

### <a name="return-value"></a>傳回值

如果授權金鑰字串不是 Null，則為非零;否則為0。

### <a name="remarks"></a>備註

此函式的預設實值會傳回0，並將任何內容儲存在 BSTR 中。 如果您使用 MFC ActiveX ControlWizard 建立專案，ControlWizard 會提供可抓取控制項授權金鑰的覆寫。

##  <a name="islicensevalid"></a>COleObjectFactory：： IsLicenseValid

判斷控制項的授權是否有效。

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>傳回值

如果 successul，則為 TRUE;否則為 false。

##  <a name="isregistered"></a>COleObjectFactory：： IsRegistered

如果 factory 已向 OLE 系統 Dll 註冊，則會傳回非零值。

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>傳回值

如果已註冊 factory，則為非零值;否則為0。

##  <a name="oncreateobject"></a>COleObjectFactory：： OnCreateObject

由架構呼叫以建立新的物件。

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>傳回值

所建立物件的指標。 如果失敗，它可能會擲回記憶體例外狀況。

### <a name="remarks"></a>備註

覆寫此函式，以從傳遞至此函式的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)以外的專案建立物件。

##  <a name="register"></a>COleObjectFactory：： Register

向 OLE 系統 Dll 註冊此物件 factory。

```
virtual BOOL Register();
```

### <a name="return-value"></a>傳回值

如果成功註冊 factory，則為非零;否則為0。

### <a name="remarks"></a>備註

此函式通常會在應用程式啟動時由[CWinApp：： InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)呼叫。

##  <a name="registerall"></a>COleObjectFactory：： RegisterAll

向 OLE 系統 Dll 註冊所有應用程式的物件 factory。

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>傳回值

如果成功註冊 factory，則為非零;否則為0。

### <a name="remarks"></a>備註

此函式通常會在應用程式啟動時由[CWinApp：： InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)呼叫。

##  <a name="revoke"></a>COleObjectFactory：： Revoke

撤銷這個物件處理站使用 OLE 系統 Dll 的註冊。

```
void Revoke();
```

### <a name="remarks"></a>備註

架構會在應用程式終止之前自動呼叫此函式。 如有需要，請從[CWinApp：： ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)的覆寫呼叫它。

##  <a name="revokeall"></a>COleObjectFactory：： RevokeAll

使用 OLE 系統 Dll 撤銷應用程式的所有物件處理站註冊。

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>備註

架構會在應用程式終止之前自動呼叫此函式。 如有需要，請從[CWinApp：： ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)的覆寫呼叫它。

##  <a name="unregisterall"></a>COleObjectFactory：： UnregisterAll

取消註冊應用程式的所有物件 factory。

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

##  <a name="updateregistry"></a>COleObjectFactory：： UpdateRegistry

向 OLE 系統登錄註冊所有應用程式的物件 factory。

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>參數

*lpszProgID*<br/>
包含人類可讀程式識別碼之字串的指標，例如 "Excel. Document. 5"。

*bRegister*<br/>
判斷是否要註冊控制項類別的物件 factory。

### <a name="remarks"></a>備註

此函式的兩個表單簡短討論如下：

- **UpdateRegistry （** `lpszProgID` **）** 向 OLE 系統登錄註冊此物件 factory。 此函式通常會在應用程式啟動時由[CWinApp：： InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)呼叫。

- **UpdateRegistry （** `bRegister` **）** 這種形式的函式是可覆寫的。 如果*bRegister*為 TRUE，則此函式會向系統登錄註冊控制項類別。 否則，它會取消註冊類別。

   如果您使用 MFC ActiveX ControlWizard 建立專案，ControlWizard 會提供此純虛擬函式的覆寫。

##  <a name="updateregistryall"></a>COleObjectFactory：： UpdateRegistryAll

向 OLE 系統登錄註冊所有應用程式的物件 factory。

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>參數

*bRegister*<br/>
判斷是否要註冊控制項類別的物件 factory。

### <a name="return-value"></a>傳回值

如果成功更新處理站，則為非零值;否則為0。

### <a name="remarks"></a>備註

此函式通常會在應用程式啟動時由[CWinApp：： InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)呼叫。

##  <a name="verifylicensekey"></a>COleObjectFactory：： VerifyLicenseKey

確認容器具有使用 OLE 控制項的授權。

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>參數

*bstrKey*<br/>
一個 BSTR，用來儲存容器的授權字串版本。

### <a name="return-value"></a>傳回值

如果執行時間授權有效，則為非零值;否則為0。

### <a name="remarks"></a>備註

預設版本會呼叫[GetLicenseKey](#getlicensekey)來取得控制項的授權字串複本，並將它與*bstrKey*中的字串進行比較。 如果兩個字串相符，函數會傳回非零值。否則，它會傳回0。

您可以覆寫此函式，以提供自訂的授權驗證。

函數[VerifyUserLicense](#verifyuserlicense)會驗證設計階段授權。

##  <a name="verifyuserlicense"></a>COleObjectFactory：： VerifyUserLicense

驗證 OLE 控制項的設計階段授權。

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>傳回值

如果設計階段授權有效，則為非零。否則為0。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer 類別](../../mfc/reference/coletemplateserver-class.md)
