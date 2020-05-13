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
ms.openlocfilehash: 9e22184a4081762a3d505645752e514315146981
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318445"
---
# <a name="csettingsstoresp-class"></a>CSettingsStoreSP 類別

該`CSettingsStoreSP`類是一個幫助器類,可用於創建[CSettingsStore 類](../../mfc/reference/csettingsstore-class.md)的實例。

## <a name="syntax"></a>語法

```
class CSettingsStoreSP
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSettingsStoreSP:CSettingsStoreSP](#csettingsstoresp)|建構 `CSettingsStoreSP` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSettingsStoreSP:創建](#create)|創建派生自`CSettingsStore`的類的實例。|
|[CSettingsStoreSP::設置運行時類](#setruntimeclass)|設置運行時類。 該方法`Create`使用運行時類來確定要創建的物件類。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|`m_dwUserData`|儲存在物件中的`CSettingsStoreSP`自定義用戶數據。 在`CSettingsStoreSP`對象的構造函數中提供此數據。|
|`m_pRegistry`|`Create`方法`CSettingsStore`創建的派生物件。|

## <a name="remarks"></a>備註

可以使用`CSettingsStoreSP`該 類將所有 MFC 註冊表操作重定向到其他位置,如 XML 檔案或資料庫。 若要這樣做，請遵循下列步驟：

1. 創建類 (`CMyStore`如 ),並從`CSettingsStore`派生 它。

1. 將[DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)和[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)`CSettingsStore`宏與自訂 類一起啟用動態創建。

1. 重寫虛擬函數,並在自定義類`Read``Write`中 實現和函數。 實現任何其他功能,將數據讀取和寫入所需位置。

1. 在應用程式中,調用`CSettingsStoreSP::SetRuntimeClass`並傳遞指向從類獲取的[CRuntimeClass 結構](../../mfc/reference/cruntimeclass-structure.md)的指標。

每當框架通常訪問註冊表時,它現在都會動態實例化自定義類,並用它來讀取或寫入數據。

`CSettingsStoreSP::SetRuntimeClass`使用全域靜態變數。 因此,一次只能提供一個自定義存儲。

## <a name="requirements"></a>需求

**標題:** afxsettingsstore.h

## <a name="csettingsstorespcreate"></a><a name="create"></a>CSettingsStoreSP:創建

創建從[CSettingsStore 類](../../mfc/reference/csettingsstore-class.md)派生的物件的新實例。

```
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>參數

*bAdmin*<br/>
[在]確定是否在管理員模式下創建`CSettingsStore`物件的布爾參數。

*b 唯讀*<br/>
[在]確定是否為唯讀訪問創建`CSettingsStore`物件的布林參數。

### <a name="return-value"></a>傳回值

對新創建`CSettingsStore`物件的引用。

### <a name="remarks"></a>備註

可以使用[方法 CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)`CSettingsStoreSP::Create`來確定 將創建的物件類型。 默認情況下,此方法創建一個`CSettingsStore`物件。

如果在管理員模式下創建`CSettingsStore`物件,則所有註冊表訪問的預設位置HKEY_LOCAL_MACHINE。 否則,所有註冊表訪問的預設位置將HKEY_CURRENT_USER。

如果*bAdmin*為 TRUE,則應用程式必須具有管理許可權。 否則,當它嘗試訪問註冊表時,它將失敗。

### <a name="example"></a>範例

下面的示例演示如何使用`Create``CSettingsStoreSP`類的方法。

[!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]

## <a name="csettingsstorespcsettingsstoresp"></a><a name="csettingsstoresp"></a>CSettingsStoreSP:CSettingsStoreSP

構造[CSettings StoreSP 類](../../mfc/reference/csettingsstoresp-class.md)物件。

```
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```

### <a name="parameters"></a>參數

*dwUserData*<br/>
[在]`CSettingsStoreSP`物件存儲的使用者定義數據。

### <a name="remarks"></a>備註

物件`CSettingsStoreSP`將*dwUserData*的數據儲存在受保護的成員`m_dwUserData`變數 中。

## <a name="csettingsstorespsetruntimeclass"></a><a name="setruntimeclass"></a>CSettingsStoreSP::設置運行時類

設置運行時類。 方法[CSettingsStoreSP:create](#create)使用運行時類來確定要創建的物件類型。

```
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```

### <a name="parameters"></a>參數

*pRTI*<br/>
[在]指向從[CSettingsStore 類](../../mfc/reference/csettingsstore-class.md)派生的類的運行時類資訊的指標。

### <a name="return-value"></a>傳回值

如果成功,則為 TRUE;如果*pRTI*識別的類不是派`CSettingsStore`生自 ,則 FALSE

### <a name="remarks"></a>備註

可以使用[CSettingsStoreSP](../../mfc/reference/csettingsstoresp-class.md)`CSettingsStore`類 從 派生類。 如果要創建派生`SetRuntimeClass``CSettingsStore`自 的自定義類的物件,請使用方法。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CSettingsStore Class](../../mfc/reference/csettingsstore-class.md)
