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
ms.openlocfilehash: 165ba7c1918c3ccc5d5d7e0bc067fba86678a3e7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753813"
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
|[COleObject 工廠:COleObject 工廠](#coleobjectfactory)|建構 `COleObjectFactory` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleObject 工廠:取得 ClassID](#getclassid)|返回此工廠創建的物件的 OLE 類 ID。|
|[COleObject 工廠::授權有效](#islicensevalid)|確定控件的許可證是否有效。|
|[COleObject 工廠:已註冊](#isregistered)|指示物件工廠是否已在 OLE 系統 DLL 中註冊。|
|[COleObject 工廠::註冊](#register)|將此物件工廠註冊到 OLE 系統 DLL。|
|[COleObject 工廠::註冊所有](#registerall)|使用 OLE 系統 DLL 註冊應用程式的所有物件工廠。|
|[COleObject 工廠:撤銷](#revoke)|復原此物件工廠在 OLE 系統 DLL 中的註冊。|
|[COleObject 工廠::撤銷所有](#revokeall)|撤銷應用程式的物件工廠在 OLE 系統 DLL 中的註冊。|
|[COleObject 工廠::取消註冊所有](#unregisterall)|取消註冊應用程式的所有物件工廠。|
|[COleObject 工廠::更新註冊](#updateregistry)|將此物件工廠註冊到 OLE 系統註冊表。|
|[COleObject 工廠::更新註冊所有](#updateregistryall)|使用 OLE 系統註冊表註冊應用程式的所有物件工廠。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[COleObject 工廠:取得授權金鑰](#getlicensekey)|從控制項的 DLL 請求唯一的金鑰。|
|[COleObject 工廠::在建立物件上](#oncreateobject)|由框架調用以創建此工廠類型的新物件。|
|[COleObject 工廠::驗證授權金鑰](#verifylicensekey)|驗證控制項嵌入的金鑰是否與容器中嵌入的密鑰匹配。|
|[COleObject 工廠::驗證使用者授權](#verifyuserlicense)|驗證該控制項是否獲得設計時使用許可。|

## <a name="remarks"></a>備註

類別`COleObjectFactory`具有用於執行以下函數的成員函數:

- 管理對象的註冊。

- 更新 OLE 系統寄存器,以及通知 OLE 物件正在運行並準備接收消息的運行時註冊。

- 通過在設計時將控制件的使用限制為許可開發人員,並在運行時將許可應用程式限制在許可應用程式,從而強制執行許可。

- 使用 OLE 系統註冊表註冊控制物件工廠。

有關物件創建的詳細資訊,請參閱[「資料物件和資料來源 (OLE)」](../../mfc/data-objects-and-data-sources-ole.md)以及[資料物件和資料來源:創建和銷毀](../../mfc/data-objects-and-data-sources-creation-and-destruction.md)」的文章。 有關註冊的更多,[請參閱註冊一](../../mfc/registration.md)文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="coleobjectfactorycoleobjectfactory"></a><a name="coleobjectfactory"></a>COleObject 工廠:COleObject 工廠

建構物件`COleObjectFactory`,將其初始化為未註冊的物件工廠,並將其添加到工廠清單中。

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

*Clsid*<br/>
此物件工廠表示的 OLE 類 ID 的引用。

*pRuntime 類別*<br/>
指向此工廠可以創建的C++對象的運行時類的指標。

*b 多實體*<br/>
指示應用程式的單個實例是否可以支援多個實例。 如果為 TRUE,則為每個請求啟動應用程式的多個實例以創建物件。

*nFlags*<br/>
包含以下一個或多個標誌:

- `afxRegDefault`將線程模型設置為線程模型=公寓。

- `afxRegInsertable`允許控制項顯示在 OLE**物件的「插入物件**」對話框中。

- `afxRegApartmentThreading`將註冊表中的線程模型設置為線程模型_公寓。

- `afxRegFreeThreading`將註冊表中的線程模型設置為線程模型_自由。

   可以組合兩個標誌`afxRegApartmentThreading``afxRegFreeThreading`並設置線程模型_兩者。 有關線程模型註冊的詳細資訊,請參閱 Windows SDK 中的[InprocServer32。](/windows/win32/com/inprocserver32)

*lpszProgID*<br/>
指向包含口頭程序識別碼(如"Microsoft Excel")的字串的指標。

### <a name="remarks"></a>備註

但是,要使用該物件,必須註冊它。

關於詳細資訊,請參閱 Windows SDK 中的[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)。

## <a name="coleobjectfactorygetclassid"></a><a name="getclassid"></a>COleObject 工廠:取得 ClassID

返回對本工廠表示的 OLE 類 ID 的引用。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>傳回值

引用此工廠表示的 OLE 類 ID。

### <a name="remarks"></a>備註

關於詳細資訊,請參閱 Windows SDK 中的[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)。

## <a name="coleobjectfactorygetlicensekey"></a><a name="getlicensekey"></a>COleObject 工廠:取得授權金鑰

從控制項的 DLL 請求唯一的許可證金鑰,並將其儲存在*pbstrKey*指向的 BSTR 中。

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>參數

*dw 保留*<br/>
保留供未來使用。

*pbstrKey*<br/>
指向將儲存授權金鑰的 BSTR 的指標。

### <a name="return-value"></a>傳回值

如果許可證密鑰字串不是 NULL,則非零;否則 0。

### <a name="remarks"></a>備註

此函數的預設實現返回 0,並且不存儲在 BSTR 中。 如果使用 MFC ActiveX ControlWizard 建立專案,ControlWizard 會提供檢索控制件許可證金鑰的重寫。

## <a name="coleobjectfactoryislicensevalid"></a><a name="islicensevalid"></a>COleObject 工廠::授權有效

確定控件的許可證是否有效。

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>傳回值

如果成功,就是真實的;否則是虛假的。

## <a name="coleobjectfactoryisregistered"></a><a name="isregistered"></a>COleObject 工廠:已註冊

如果工廠在 OLE 系統 DLL 中註冊,則返回非零值。

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>傳回值

如果工廠已註冊,則非零;否則 0。

## <a name="coleobjectfactoryoncreateobject"></a><a name="oncreateobject"></a>COleObject 工廠::在建立物件上

由框架調用以創建新物件。

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>傳回值

指向創建物件的指標。 如果失敗,可能會引發記憶體異常。

### <a name="remarks"></a>備註

重寫此函數,以便從傳遞給建構函數的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)以外的內容創建物件。

## <a name="coleobjectfactoryregister"></a><a name="register"></a>COleObject 工廠::註冊

將此物件工廠註冊到 OLE 系統 DLL。

```
virtual BOOL Register();
```

### <a name="return-value"></a>傳回值

如果工廠已成功註冊,則非零;否則 0。

### <a name="remarks"></a>備註

此函數通常由[CWinApp::在](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時調用 IninInstance。

## <a name="coleobjectfactoryregisterall"></a><a name="registerall"></a>COleObject 工廠::註冊所有

使用 OLE 系統 DLL 註冊應用程式的所有物件工廠。

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>傳回值

如果工廠成功註冊,則非零;否則 0。

### <a name="remarks"></a>備註

此函數通常由[CWinApp::在](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時調用 IninInstance。

## <a name="coleobjectfactoryrevoke"></a><a name="revoke"></a>COleObject 工廠:撤銷

復原此物件工廠在 OLE 系統 DLL 中的註冊。

```cpp
void Revoke();
```

### <a name="remarks"></a>備註

框架在應用程式終止之前自動調用此函數。 如有必要,請從[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)的重寫調用它。

## <a name="coleobjectfactoryrevokeall"></a><a name="revokeall"></a>COleObject 工廠::撤銷所有

撤銷應用程式在 OLE 系統 DLL 上的所有物件工廠的註冊。

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>備註

框架在應用程式終止之前自動調用此函數。 如有必要,請從[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)的重寫調用它。

## <a name="coleobjectfactoryunregisterall"></a><a name="unregisterall"></a>COleObject 工廠::取消註冊所有

取消註冊應用程式的所有物件工廠。

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

## <a name="coleobjectfactoryupdateregistry"></a><a name="updateregistry"></a>COleObject 工廠::更新註冊

使用 OLE 系統註冊表註冊應用程式的所有物件工廠。

```cpp
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>參數

*lpszProgID*<br/>
指向包含人可讀程序標識符(如"Excel.Document.5")的字串的指標。

*b 註冊*<br/>
確定是否應註冊控件類的物件工廠。

### <a name="remarks"></a>備註

此函數的兩種形式的簡要討論如下:

- **更新註冊處)** `lpszProgID` **)** 將此物件工廠註冊到 OLE 系統註冊表。 此函數通常由[CWinApp::在](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時調用 IninInstance。

- **更新註冊處)** `bRegister` **)** 函數的這種形式是可重寫的。 如果*b 寄存器*為 TRUE,則此函數將控制類註冊到系統註冊表中。 否則,它將取消註冊類。

   如果使用 MFC ActiveX ControlWizard 創建專案,ControlWizard 會為此純虛擬函數提供覆蓋。

## <a name="coleobjectfactoryupdateregistryall"></a><a name="updateregistryall"></a>COleObject 工廠::更新註冊所有

使用 OLE 系統註冊表註冊應用程式的所有物件工廠。

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>參數

*b 註冊*<br/>
確定是否應註冊控件類的物件工廠。

### <a name="return-value"></a>傳回值

如果成功更新工廠,則非零;否則 0。

### <a name="remarks"></a>備註

此函數通常由[CWinApp::在](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時調用 IninInstance。

## <a name="coleobjectfactoryverifylicensekey"></a><a name="verifylicensekey"></a>COleObject 工廠::驗證授權金鑰

驗證容器是否被許可使用 OLE 控制項。

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>參數

*bstrKey*<br/>
儲存容器版本的許可證字串的 BSTR。

### <a name="return-value"></a>傳回值

如果運行時許可證有效,則非零;否則 0。

### <a name="remarks"></a>備註

默認版本調用[GetLicenseKey](#getlicensekey)獲取控制項的許可證字串的副本,並將其與*bstrKey*中的字串進行比較。 如果兩個字串匹配,則函數返回一個非零值;如果兩個字串匹配,則函數將返回一個非零值。否則它返回 0。

您可以重寫此函數以提供許可證的自定義驗證。

功能[驗證使用者許可證](#verifyuserlicense)驗證設計時許可證。

## <a name="coleobjectfactoryverifyuserlicense"></a><a name="verifyuserlicense"></a>COleObject 工廠::驗證使用者授權

驗證 OLE 控制項設計時使用許可證。

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>傳回值

如果設計時許可證有效,則非零;否則 0。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer 類別](../../mfc/reference/coletemplateserver-class.md)
