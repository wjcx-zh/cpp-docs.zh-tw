---
title: 標準對話方塊資料交換常式
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 83d4a66cd3ec41008506b55f0b351fd9bcbc24b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372923"
---
# <a name="standard-dialog-data-exchange-routines"></a>標準對話方塊資料交換常式

本主題列出了用於常見 MFC 對話方塊控制件的標準對話框資料交換 (DDX) 例程。

> [!NOTE]
> 標準對話框資料交換例程在標頭檔 afxdd_.h 中定義。 但是,應用程式應包括 afxwin.h。

### <a name="ddx-functions"></a>DDX 功能

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|初始化或檢索組合框控制項的當前選擇的索引。|
|[DDX_CBString](#ddx_cbstring)|初始化或檢索組合框控制件的編輯欄位的當前內容。|
|[DDX_CBStringExact](#ddx_cbstringexact)|初始化或檢索組合框控制件的編輯欄位的當前內容。|
|[DDX_Check](#ddx_check)|初始化或檢索複選框控制項的當前狀態。|
|[DDX_Control](#ddx_control)|在對話框中對給定控制件進行子類。|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|初始化或檢索日期和時間選取器控制項的日期和/或時間數據。|
|[DDX_IPAddress](#ddx_ipaddress)|初始化或檢索 IP 位址控制項的目前值。|
|[DDX_LBIndex](#ddx_lbindex)|初始化或檢索清單框控制件的當前選擇的索引。|
|[DDX_LBString](#ddx_lbstring)|在清單框控制項中初始化或檢索當前選擇。|
|[DDX_LBStringExact](#ddx_lbstringexact)|在清單框控制項中初始化或檢索當前選擇。|
|[DDX_ManagedControl](#ddx_managedcontrol)|建立與控制項的資源 ID 符合的 .NET 控制項。|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|初始化或檢索月份日曆控制件的當前值。|
|[DDX_Radio](#ddx_radio)|初始化或檢索當前在無線電控制組中檢查的無線電控制項的 0 個基於 0 的索引。|
|[DDX_Scroll](#ddx_scroll)|初始化或檢索滾動控件拇指的當前位置。|
|[DDX_Slider](#ddx_slider)|初始化或檢索滑塊控制項拇指的目前位置。|
|[DDX_Text](#ddx_text)|初始化或檢索編輯控制項的當前值。|

## <a name="ddx_cbindex"></a><a name="ddx_cbindex"></a>DDX_CBIndex

該`DDX_CBIndex`函數管理在對話框、表單檢視或控制元件檢視物件中的組合框控制項和對話框、窗體檢視或控制元件檢視物件的**int**資料成員之間的**int**資料傳輸。

```cpp
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性關聯的組合框控制件的資源 ID。

*指數*<br/>
對對話框、表單元件檢視或控制件檢視物件的成員變數的引用,用於交換數據。

### <a name="remarks"></a>備註

呼叫`DDX_CBIndex`時,*索引*將設定為目前組合框選擇的索引。 如果未選擇任何項,*則索引*設定為 0。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_cbstring"></a><a name="ddx_cbstring"></a>DDX_CBString

該`DDX_CBString`函數管理對話框、表`CString`單檢視或控制項檢視物件組合框控制項的編輯控制件與對話框、表單圖像檢視或控制元件檢視物件`CString`的資料傳輸。

```cpp
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性關聯的組合框控制件的資源 ID。

*值*<br/>
對對話框、表單元件檢視或控制件檢視物件的成員變數的引用,用於交換數據。

### <a name="remarks"></a>備註

呼叫`DDX_CBString`時,*值*設定為當前組合框選擇。 如果未選擇任何項,*則值*將設定為長度為零的字串。

> [!NOTE]
> 如果組合框是下拉列表框,則交換的值限制為 255 個字元。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_cbstringexact"></a><a name="ddx_cbstringexact"></a>DDX_CBStringExact

該`DDX_CBStringExact`函數管理對話框、表`CString`單檢視或控制項檢視物件組合框控制項的編輯控制件與對話框、表單圖像檢視或控制元件檢視物件`CString`的資料傳輸。

```cpp
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性關聯的組合框控制件的資源 ID。

*值*<br/>
對對話框、表單元件檢視或控制件檢視物件的成員變數的引用,用於交換數據。

### <a name="remarks"></a>備註

呼叫`DDX_CBStringExact`時,*值*設定為當前組合框選擇。 如果未選擇任何項,*則值*將設定為長度為零的字串。

> [!NOTE]
> 如果組合框是下拉列表框,則交換的值限制為 255 個字元。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_check"></a><a name="ddx_check"></a>DDX_Check

該`DDX_Check`函數管理在對話框、表單檢視或控制項檢視物件的複選框控制項和對話框、表單檢視或控制元件檢視物件的**int**資料成員之間傳輸**int**資料。

```cpp
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性關聯的複選框控制項的資源 ID。

*值*<br/>
對對話框、表單元件檢視或控制件檢視物件的成員變數的引用,用於交換數據。

### <a name="remarks"></a>備註

呼叫`DDX_Check`時,*值*設定為複選框控制的目前狀態。 有關可能的狀態值的清單,請參閱 Windows SDK 中的[BM_GETCHECK。](/windows/win32/Controls/bm-getcheck)

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_control"></a><a name="ddx_control"></a>DDX_Control

函數`DDX_Control`對對話框、表單檢視或控制項檢視物件的控制項,由*nIDC*指定。

```cpp
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*nIDC*<br/>
要子類的控制項的資源 ID。

*r控制*<br/>
對對話框、窗體視圖或控件視圖物件的成員變數的引用,該變數與指定的控制項相關。

### <a name="remarks"></a>備註

當調用`DoDataExchange`函數時 *,pDX*物件由框架提供。 因此,`DDX_Control`只能在對`DoDataExchange`的重寫中呼叫 。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_datetimectrl"></a><a name="ddx_datetimectrl"></a>DDX_DateTimeCtrl

該`DDX_DateTimeCtrl`函數管理日期和時間選取器控制項[(CDateTimeCtrl)](../../mfc/reference/cdatetimectrl-class.md)在對話框或窗體檢視物件以及對話框或窗體檢視物件的[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)資料成員之間的日期和/或時間資料的傳輸。

```cpp
void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。 您無需刪除此物件。

*nIDC*<br/>
與成員變數關聯的日期和時間選取器控制項的資源 ID。

*值*<br/>
在前兩個版本中,對交換數據的或`CTime``COleDateTime`成員變數、對話框、窗體視圖或控件視圖物件的引用。 在第三個版本中,對`CString`數據成員控件視圖物件的引用。

### <a name="remarks"></a>備註

呼叫`DDX_DateTimeCtrl`時,*值*設定為日期和時間選取器控制項的當前狀態,或者控制項設定為*值*,具體取決於交換的方向。

在上面的第三個版本中,`DDX_DateTimeCtrl`管理日期時間控制`CString`件 和控制檢視物件的[CString](../../atl-mfc-shared/reference/cstringt-class.md)數據成員之間的數據傳輸。 字串使用當前區域設置的規則格式化日期和時間。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_managedcontrol"></a><a name="ddx_managedcontrol"></a>DDX_ManagedControl

建立與控制項的資源 ID 符合的 .NET 控制項。

### <a name="syntax"></a>語法

```cpp
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange 類](cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性關聯的控制項的資源識別碼。

*控制*<br/>
對[CWinForms 控制類](cwinformscontrol-class.md)物件的引用。

### <a name="remarks"></a>備註

`DDX_ManagedControl`呼叫[CWinForms 控制::建立託管控制](cwinformscontrol-class.md#createmanagedcontrol)以建立與資源控制 ID 符合的控制項。 從`DDX_ManagedControl`CDialog 中從資源代碼建立控制項[:onInitDialog](cdialog-class.md#oninitdialog)。 對於資料交換,您無需將 DDX/DDV 函數與 Windows 窗體控制項一起使用。

有關詳細資訊,請參閱[如何:使用 Windows 窗體 進行 DDX/DDV 資料繫結 。](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

### <a name="requirements"></a>需求

**標題:** afxwinforms.h

## <a name="ddx_ipaddress"></a><a name="ddx_ipaddress"></a>DDX_IPAddress

該`DDX_IPAddress`函數管理 IP 位址控制件和控制檢視物件的資料成員之間的資料傳輸。

```cpp
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性關聯的 IP 位址控制的資源 ID。

*值*<br/>
對包含 IP 位址控制件的四欄位值的 DWORD 的引用。 欄位填充或讀取如下。

|欄位|引入欄位值的位元|
|-----------|-------------------------------------|
|3|0 到 7|
|2|8 到 15|
|1|16 到 23|
|0|24 到 31|

使用 Win32 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress)讀取該值,或使用[IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)填充該值。 這些消息在 Windows SDK 中描述。

### <a name="remarks"></a>備註

呼叫`DDX_IPAddress`時,*值*要麼從 IP 位址控制件讀取 *,要麼根據*交換的方向寫入控制項。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_lbindex"></a><a name="ddx_lbindex"></a>DDX_LBIndex

該`DDX_LBIndex`函數管理在對話框、表單檢視或控制元件檢視物件中的清單框控制項和對話框、窗體檢視或控制元件檢視物件的**int**資料成員之間的**int**資料傳輸。

```cpp
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性關聯的清單框控制件的資源 ID。

*指數*<br/>
對對話框、表單元件檢視或控制件檢視物件的成員變數的引用,用於交換數據。

### <a name="remarks"></a>備註

呼叫`DDX_LBIndex`時,*索引*將設定為目前清單框選擇的索引。 如果未選擇任何項,*則索引*設置為 -1。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_lbstring"></a><a name="ddx_lbstring"></a>DDX_LBString

該`DDX_LBString`函數管理對話框、表`CString`單檢視或控制項檢視物件中的清單框控制項與對話框、窗體視圖或控制元件檢視物件`CString`的資料成員之間的資料傳輸。

```cpp
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性關聯的清單框控制件的資源 ID。

*值*<br/>
對對話框、表單元件檢視或控制件檢視物件的成員變數的引用,用於交換數據。

### <a name="remarks"></a>備註

當`DDX_LBString`調用將數據傳輸到列表框控制項時,將選擇其開始匹配*值*的控制項中的第一個項。 (要匹配整個專案,而不僅僅是前置字,請使用[DDX_LBStringExact](#ddx_lbstringexact)。如果沒有匹配項,則不選擇任何專案。 匹配不區分大小寫。

當`DDX_LBString`調用從清單框控制元件傳輸資料時,*值*將設置為當前清單框選擇。 如果未選擇任何項,*則值*將設定為長度為零的字串。

> [!NOTE]
> 如果清單框是下拉列表框,則交換的值限制為 255 個字元。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_lbstringexact"></a><a name="ddx_lbstringexact"></a>DDX_LBStringExact

該`DDX_CBStringExact`函數管理對話框、表`CString`單檢視或控制項檢視物件中列表框控制項的編輯控制件與對話框、窗體檢視或控制元件檢視物件`CString`的資料傳輸。

```cpp
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性關聯的清單框控制件的資源 ID。

*值*<br/>
對對話框、表單元件檢視或控制件檢視物件的成員變數的引用,用於交換數據。

### <a name="remarks"></a>備註

當`DDX_LBStringExact`調用將數據傳輸到列表框控制項時,將選擇控制項中與*值*匹配的第一項。 (要僅符合前置碼而不是整個項目,請使用[DDX_LBString](#ddx_lbstring)。如果沒有匹配項,則不選擇任何專案。 匹配不區分大小寫。

當`DDX_CBStringExact`調用從清單框控制元件傳輸資料時,*值*將設置為當前清單框選擇。 如果未選擇任何項,*則值*將設定為長度為零的字串。

> [!NOTE]
> 如果清單框是下拉列表框,則交換的值限制為 255 個字元。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_monthcalctrl"></a><a name="ddx_monthcalctrl"></a>DDX_MonthCalCtrl

該`DDX_MonthCalCtrl`函數管理在對話框、窗體檢視或控制項檢視物件以及對話框[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)、窗體視圖或控制項檢視物件的[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)資料成員之間的日期數據傳輸。

```cpp
void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。 您無需刪除此物件。

*nIDC*<br/>
與成員變數關聯的月份日曆控制件的資源 ID。

*值*<br/>
對對話框、表單`CTime`元件檢視`COleDateTime`或控制元件檢視物件的 或成員變數的引用,用於交換數據。

### <a name="remarks"></a>備註

> [!NOTE]
> 控制項僅管理日期值。 時間物件中的時間欄位設定為反映控制項視窗的建立時間,或者控制項中設定的任何時間以及呼叫`CMonthCalCtrl::SetCurSel`。

呼叫`DDX_MonthCalCtrl`時,*值*設定為月曆控件的當前狀態。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_radio"></a><a name="ddx_radio"></a>DDX_Radio

該`DDX_Radio`函數管理在對話框、表單檢視或控制元件檢視物件中的無線電控制組和對話框、窗體檢視或控制元件檢視物件的**int**資料成員之間的**int**資料傳輸。 **int**資料成員的值根據組中的哪個單選按鈕確定。

```cpp
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
組中第一個無線電控制件的資源ID。

*值*<br/>
對對話框、表單元件檢視或控制件檢視物件的成員變數的引用,用於交換數據。

### <a name="remarks"></a>備註

呼叫`DDX_Radio`時,*值*設定為無線電控制組的當前狀態。 該值設置為當前檢查的無線電控件的 0 個索引,如果未檢查無線電控件,則設置為 -1。

例如,如果選中組中的第一個單選按鈕(具有WS_GROUP樣式的按鈕 **),int**成員的值為 0,等等。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_scroll"></a><a name="ddx_scroll"></a>DDX_Scroll

該`DDX_Scroll`函數管理在對話框、表單檢視或控制元件檢視物件中的滾動條控制項和對話框、窗體視圖或控制元件檢視物件的**int**資料成員之間的**int**資料傳輸。

```cpp
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
`CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性關聯的滾動條控制項的資源 ID。

*值*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

呼叫`DDX_Scroll`時,*值*設定為控制項拇指的目前位置。 有關與控制項的拇指當前位置關聯的值的詳細資訊,請參閱 Windows SDK 中的[GetScrollPos。](/windows/win32/api/winuser/nf-winuser-getscrollpos)

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_slider"></a><a name="ddx_slider"></a>DDX_Slider

該`DDX_Slider`函數管理在對話框或表單圖中的滑塊控制件和對話框或窗體視圖物件的**int**資料成員之間的**int**資料傳輸。

```cpp
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
滑塊控制件的資源 ID。

*值*<br/>
對要交換的值的引用。 此參數保留或設置滑塊控制項的當前位置。

### <a name="remarks"></a>備註

呼叫`DDX_Slider`時,*值*設定為控制項拇指的當前位置,或者該值接收位置,具體取決於交換的方向。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 有關滑動項資訊,請參閱[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="ddx_text"></a><a name="ddx_text"></a>DDX_Text

該`DDX_Text`函數管理在對話框、窗體檢視或控件檢視的編輯控件**long**和對話框、窗體檢視`CString`或控制件檢視物件的[CString](../../atl-mfc-shared/reference/cstringt-class.md)數據成員之間的 int、UINT、長、DWORD、float 或**雙資料**之間的傳輸。 **int** **UINT** **float**

```cpp
void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    short& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    int& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    UINT& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    long& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    CString& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    float& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    double& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話框、表單檢視或控制檢視物件中編輯控制件的識別碼。

*值*<br/>
對對話框、窗體視圖或控件視圖物件中的數據成員的引用。 *值*的資料`DDX_Text`類型取決於 您使用的重載版本。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標題**afxdd_.h

## <a name="see-also"></a>另請參閱

[標準對話方塊資料驗證常式](standard-dialog-data-validation-routines.md)<br/>
[巨集和全域](mfc-macros-and-globals.md)<br/>
[CWinForms控制:建立託管控制](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog:onInitDialog](cdialog-class.md#oninitdialog)
