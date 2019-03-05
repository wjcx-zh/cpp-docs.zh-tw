---
title: CSettingsStoreSP 類別
ms.date: 11/04/2016
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
helpviewer_keywords:
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
ms.openlocfilehash: 5c7a992b983552340ebe21e59d2ee9a667841ec0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275190"
---
# <a name="csettingsstoresp-class"></a>CSettingsStoreSP 類別

`CSettingsStoreSP`類別是一個 helper 類別，您可以使用建立的執行個體[CSettingsStore 類別](../../mfc/reference/csettingsstore-class.md)。

## <a name="syntax"></a>語法

```
class CSettingsStoreSP
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSettingsStoreSP::CSettingsStoreSP](#csettingsstoresp)|建構 `CSettingsStoreSP` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSettingsStoreSP::Create](#create)|建立衍生自類別的執行個體`CSettingsStore`。|
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|設定執行階段類別。 `Create`方法來判斷哪些類別的物件，以建立會使用執行階段類別。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|`m_dwUserData`|自訂使用者資料儲存在`CSettingsStoreSP`物件。 您提供的建構函式中的這個資料`CSettingsStoreSP`物件。|
|`m_pRegistry`|`CSettingsStore`-衍生物件`Create`方法會建立。|

## <a name="remarks"></a>備註

您可以使用`CSettingsStoreSP`類別，以將所有的 MFC 登錄作業重新導向至其他位置，例如 XML 檔案或資料庫。 若要執行此動作，請依照下列步驟執行：

1. 建立類別 (例如`CMyStore`)，並從它衍生`CSettingsStore`。

1. 使用[DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)並[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)巨集與您的自訂`CSettingsStore`以啟用動態建立的類別。

1. 覆寫虛擬函式，並實作`Read`和`Write`函式，在您的自訂類別。 實作任何其他功能，以便讀取和寫入資料到您想要的位置。

1. 在您的應用程式中，呼叫`CSettingsStoreSP::SetRuntimeClass`，並傳入的指標[CRuntimeClass 結構](../../mfc/reference/cruntimeclass-structure.md)取自您的類別。

每當此架構通常會存取登錄，它會立即以動態方式具現化您的自訂類別，並用來讀取或寫入資料。

`CSettingsStoreSP::SetRuntimeClass` 使用全域靜態變數。 因此，只有一個自訂存放區可一次。

## <a name="requirements"></a>需求

**標頭：** afxsettingsstore.h

##  <a name="create"></a>  CSettingsStoreSP::Create

建立新的執行個體的物件衍生自[CSettingsStore 類別](../../mfc/reference/csettingsstore-class.md)。

```
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>參數

*bAdmin*<br/>
[in]布林值參數，決定是否`CSettingsStore`系統管理員模式中建立物件。

*bReadOnly*<br/>
[in]布林值參數，決定是否`CSettingsStore`建立物件的唯讀存取權。

### <a name="return-value"></a>傳回值

新建立的參考`CSettingsStore`物件。

### <a name="remarks"></a>備註

您可以使用的方法[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)來判斷何種物件`CSettingsStoreSP::Create`會建立。 根據預設，這個方法會建立`CSettingsStore`物件。

如果您建立`CSettingsStore`物件在系統管理員模式中，所有的登錄存取權的預設位置是 HKEY_LOCAL_MACHINE。 否則，所有的登錄存取權的預設位置是 HKEY_CURRENT_USER。

如果*bAdmin*為 TRUE 時，應用程式必須具備系統管理權限。 否則，它將會失敗時嘗試存取登錄。

### <a name="example"></a>範例

下列範例示範如何使用`Create`方法的`CSettingsStoreSP`類別。

[!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]

##  <a name="csettingsstoresp"></a>  CSettingsStoreSP::CSettingsStoreSP

建構[CSettingsStoreSP 類別](../../mfc/reference/csettingsstoresp-class.md)物件。

```
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```

### <a name="parameters"></a>參數

*dwUserData*<br/>
[in]使用者定義的資料，`CSettingsStoreSP`物件存放區。

### <a name="remarks"></a>備註

`CSettingsStoreSP`物件會儲存的資料*dwUserData*受保護的成員變數中`m_dwUserData`。

##  <a name="setruntimeclass"></a>  CSettingsStoreSP::SetRuntimeClass

設定執行階段類別。 此方法[CSettingsStoreSP::Create](#create)用以決定要建立的物件類型的執行階段類別。

```
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```

### <a name="parameters"></a>參數

*pRTI*<br/>
[in]從衍生類別的執行階段類別資訊指標[CSettingsStore 類別](../../mfc/reference/csettingsstore-class.md)。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE如果所識別的類別，則為 FALSE。 *pRTI*不衍生自`CSettingsStore`。

### <a name="remarks"></a>備註

您可以使用[CSettingsStoreSP 類別](../../mfc/reference/csettingsstoresp-class.md)衍生類別，從`CSettingsStore`。 使用方法`SetRuntimeClass`如果您想要建立的自訂類別衍生自物件`CSettingsStore`。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CSettingsStore 類別](../../mfc/reference/csettingsstore-class.md)
