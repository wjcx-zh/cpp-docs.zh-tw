---
title: 標準對話方塊資料交換常式
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: bed60094b25bcc3b1994aa904a8c20324be2abae
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844492"
---
# <a name="standard-dialog-data-exchange-routines"></a>標準對話方塊資料交換常式

本主題列出一般 MFC 對話方塊控制項所使用的標準對話方塊資料交換 (DDX) 常式。

> [!NOTE]
> 標準對話方塊資料交換常式會定義在標頭檔 afxdd_ .h 中。 不過，應用程式應該包含 afxwin.h。

### <a name="ddx-functions"></a>DDX 函數

|名稱|描述|
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|初始化或抓取下拉式方塊控制項目前選取範圍的索引。|
|[DDX_CBString](#ddx_cbstring)|初始化或抓取下拉式方塊控制項之編輯欄位的目前內容。|
|[DDX_CBStringExact](#ddx_cbstringexact)|初始化或抓取下拉式方塊控制項之編輯欄位的目前內容。|
|[DDX_Check](#ddx_check)|初始化或抓取核取方塊控制項的目前狀態。|
|[DDX_Control](#ddx_control)|子類別：對話方塊內的特定控制項。|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|初始化或抓取日期和時間選擇器控制項的日期和/或時間資料。|
|[DDX_IPAddress](#ddx_ipaddress)|初始化或抓取 IP 位址控制項的目前值。|
|[DDX_LBIndex](#ddx_lbindex)|初始化或抓取清單方塊控制項目前選取範圍的索引。|
|[DDX_LBString](#ddx_lbstring)|初始化或抓取清單方塊控制項中目前的選取範圍。|
|[DDX_LBStringExact](#ddx_lbstringexact)|初始化或抓取清單方塊控制項中目前的選取範圍。|
|[DDX_ManagedControl](#ddx_managedcontrol)|建立符合控制項資源識別碼的 .NET 控制項。|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|初始化或抓取月曆控制項的目前值。|
|[DDX_Radio](#ddx_radio)|初始化或抓取目前在單選控制項群組內檢查之選項按鈕控制項的以零為起始的索引。|
|[DDX_Scroll](#ddx_scroll)|初始化或抓取捲軸控制項捲動方塊的目前位置。|
|[DDX_Slider](#ddx_slider)|初始化或抓取滑杆控制項捲動方塊的目前位置。|
|[DDX_Text](#ddx_text)|初始化或抓取編輯控制項的目前值。|

## <a name="ddx_cbindex"></a><a name="ddx_cbindex"></a> DDX_CBIndex

函式會 `DDX_CBIndex` 管理 **`int`** 對話方塊中的下拉式方塊控制項、表單檢視或控制項視圖物件的組合，以及 **`int`** 對話方塊、表單檢視或 control view 物件的資料成員之間的資料傳輸。

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
與控制項屬性相關聯之下拉式方塊控制項的資源識別碼。

*index*<br/>
對話方塊的成員變數參考、表單檢視，或是用來交換資料的 control view 物件。

### <a name="remarks"></a>備註

當 `DDX_CBIndex` 呼叫時， *索引* 會設定為目前下拉式方塊選取範圍的索引。 如果未選取任何專案，則會將 *索引* 設定為0。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_cbstring"></a><a name="ddx_cbstring"></a> DDX_CBString

此函式會在 `DDX_CBString` `CString` 對話方塊、表單檢視或控制項視圖物件的編輯控制項，以及 `CString` 對話方塊、表單檢視或 control view 物件的資料成員之間，管理資料的傳輸。

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
與控制項屬性相關聯之下拉式方塊控制項的資源識別碼。

*value*<br/>
對話方塊的成員變數參考、表單檢視，或是用來交換資料的 control view 物件。

### <a name="remarks"></a>備註

當 `DDX_CBString` 呼叫時， *值* 會設定為目前的下拉式方塊選取範圍。 如果未選取任何專案，則 *值* 會設定為長度為零的字串。

> [!NOTE]
> 如果下拉式方塊是下拉式清單方塊，則會將交換的值限制為255個字元。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_cbstringexact"></a><a name="ddx_cbstringexact"></a> DDX_CBStringExact

此函式會在 `DDX_CBStringExact` `CString` 對話方塊、表單檢視或控制項視圖物件的編輯控制項，以及 `CString` 對話方塊、表單檢視或 control view 物件的資料成員之間，管理資料的傳輸。

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
與控制項屬性相關聯之下拉式方塊控制項的資源識別碼。

*value*<br/>
對話方塊的成員變數參考、表單檢視，或是用來交換資料的 control view 物件。

### <a name="remarks"></a>備註

當 `DDX_CBStringExact` 呼叫時， *值* 會設定為目前的下拉式方塊選取範圍。 如果未選取任何專案，則 *值* 會設定為長度為零的字串。

> [!NOTE]
> 如果下拉式方塊是下拉式清單方塊，則會將交換的值限制為255個字元。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_check"></a><a name="ddx_check"></a> DDX_Check

此函式會 `DDX_Check` 管理 **`int`** 對話方塊中核取方塊控制項、表單檢視或控制項視圖物件的資料傳輸 **`int`** ，以及對話方塊、表單檢視或 control view 物件的資料成員之間的資料傳輸。

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
與控制項屬性相關聯之核取方塊控制項的資源識別碼。

*value*<br/>
對話方塊的成員變數參考、表單檢視，或是用來交換資料的 control view 物件。

### <a name="remarks"></a>備註

當 `DDX_Check` 呼叫時， *值* 會設定為核取方塊控制項的目前狀態。 如需可能狀態值的清單，請參閱 Windows SDK 中的 [BM_GETCHECK](/windows/win32/Controls/bm-getcheck) 。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_control"></a><a name="ddx_control"></a> DDX_Control

此函式會子 `DDX_Control` 類別化對話方塊、表單檢視或 control view 物件所指定的控制項（由 *nIDC*所指定）。

```cpp
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>參數

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*nIDC*<br/>
要子類別化之控制項的資源識別碼。

*rControl*<br/>
與指定的控制項相關之對話方塊、表單檢視或控制項視圖物件之成員變數的參考。

### <a name="remarks"></a>備註

呼叫函數時，架構會提供 *pDX* 物件 `DoDataExchange` 。 因此， `DDX_Control` 只能在您的覆寫內呼叫 `DoDataExchange` 。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_datetimectrl"></a><a name="ddx_datetimectrl"></a> DDX_DateTimeCtrl

此函式會管理日期和 `DDX_DateTimeCtrl` 時間選擇器控制項之間的日期和/或時間資料傳輸 ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md) 對話方塊或表單檢視物件中的) ，以及對話方塊或表單檢視物件的 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 或 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 資料成員之間的傳輸。

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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。 您不需要刪除此物件。

*nIDC*<br/>
與成員變數相關聯之日期和時間選擇器控制項的資源識別碼。

*value*<br/>
在前兩個版本中，參考至 `CTime` 或 `COleDateTime` 成員變數、對話方塊、表單檢視，或用來交換資料的 control view 物件。 在第三個版本中，是 `CString` 資料成員控制 view 物件的參考。

### <a name="remarks"></a>備註

當 `DDX_DateTimeCtrl` 呼叫時，會將 *值* 設為日期和時間選擇器控制項的目前狀態，或將控制項設定為 [ *值*]，視交換的方向而定。

在上述的第三個版本中， `DDX_DateTimeCtrl` 管理 `CString` 資料在 [控制視圖] 物件的日期時間控制項和 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 資料成員之間的傳輸。 字串會使用目前地區設定的日期和時間規則來格式化。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_managedcontrol"></a><a name="ddx_managedcontrol"></a> DDX_ManagedControl

建立符合控制項資源識別碼的 .NET 控制項。

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
[CDataExchange 類別](cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
與控制項屬性相關聯之控制項的資源識別碼。

*control*<br/>
[CWinFormsControl 類別](cwinformscontrol-class.md)物件的參考。

### <a name="remarks"></a>備註

`DDX_ManagedControl` 呼叫 [CWinFormsControl：： CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) 來建立符合資源控制識別碼的控制項。 用 `DDX_ManagedControl` 來從 [CDialog：： OnInitDialog](cdialog-class.md#oninitdialog)中的資源識別碼建立控制項。 針對資料交換，您不需要搭配 Windows Forms 控制項來使用 DDX/DDV 函數。

如需詳細資訊，請參閱 [如何：使用 Windows Forms 執行 DDX/DDV 資料](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)系結。

### <a name="requirements"></a>規格需求

**標頭：** afxwinforms。h

## <a name="ddx_ipaddress"></a><a name="ddx_ipaddress"></a> DDX_IPAddress

此函 `DDX_IPAddress` 式會管理 IP 位址控制項與 control view 物件的資料成員之間的資料傳輸。

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
與控制項屬性相關聯之 IP 位址控制項的資源識別碼。

*value*<br/>
DWORD 的參考，其中包含 IP 位址控制項的四個域值。 這些欄位會填入或讀取，如下所示。

|欄位|包含域值的位|
|-----------|-------------------------------------|
|3|0到7|
|2|8到15|
|1|16到23|
|0|24到31|

使用 Win32 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress) 讀取值，或使用 [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress) 來填滿值。 Windows SDK 中會說明這些訊息。

### <a name="remarks"></a>備註

當 `DDX_IPAddress` 呼叫時，會從 IP 位址控制項讀取 *值* ，或將 *值* 寫入至控制項，視交換的方向而定。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_lbindex"></a><a name="ddx_lbindex"></a> DDX_LBIndex

此函式會 `DDX_LBIndex` 管理 **`int`** 對話方塊中的清單方塊控制項、表單檢視或控制視圖物件，以及 **`int`** 對話方塊、表單檢視或 control view 物件的資料成員之間的資料傳輸。

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
與控制項屬性相關聯之清單方塊控制項的資源識別碼。

*index*<br/>
對話方塊的成員變數參考、表單檢視，或是用來交換資料的 control view 物件。

### <a name="remarks"></a>備註

當 `DDX_LBIndex` 呼叫時， *索引* 會設定為目前清單方塊選取範圍的索引。 如果未選取任何專案，則會將 *索引* 設定為-1。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_lbstring"></a><a name="ddx_lbstring"></a> DDX_LBString

此函式會 `DDX_LBString` 管理 `CString` 對話方塊中的清單方塊控制項、表單檢視或控制視圖物件，以及 `CString` 對話方塊、表單檢視或 control view 物件的資料成員之間的資料傳輸。

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
與控制項屬性相關聯之清單方塊控制項的資源識別碼。

*value*<br/>
對話方塊的成員變數參考、表單檢視，或是用來交換資料的 control view 物件。

### <a name="remarks"></a>備註

當 `DDX_LBString` 呼叫來將資料傳送至清單方塊控制項時，會選取開始符合 *值* 之控制項中的第一個專案。  (符合整個專案，而不只是前置詞，請使用 [DDX_LBStringExact](#ddx_lbstringexact)。 ) 如果沒有相符專案，則不會選取任何專案。 比對不區分大小寫。

當 `DDX_LBString` 呼叫以從清單方塊控制項傳送資料時， *值* 會設定為目前的清單方塊選取專案。 如果未選取任何專案，則 *值* 會設定為長度為零的字串。

> [!NOTE]
> 如果清單方塊是一個下拉式清單方塊，則會將交換的值限制為255個字元。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_lbstringexact"></a><a name="ddx_lbstringexact"></a> DDX_LBStringExact

函式會在 `DDX_CBStringExact` `CString` 對話方塊、表單檢視或控制視圖物件以及 `CString` 對話方塊、表單檢視或 control view 物件的資料成員中，管理清單方塊控制項的編輯控制項之間的資料傳輸。

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
與控制項屬性相關聯之清單方塊控制項的資源識別碼。

*value*<br/>
對話方塊的成員變數參考、表單檢視，或是用來交換資料的 control view 物件。

### <a name="remarks"></a>備註

當 `DDX_LBStringExact` 呼叫來將資料傳送至清單方塊控制項時，會選取控制項中符合 *值* 的第一個專案。  (只會比對前置詞，而不是整個專案，請使用 [DDX_LBString](#ddx_lbstring)。 ) 如果沒有相符專案，則不會選取任何專案。 比對不區分大小寫。

當 `DDX_CBStringExact` 呼叫以從清單方塊控制項傳送資料時， *值* 會設定為目前的清單方塊選取專案。 如果未選取任何專案，則 *值* 會設定為長度為零的字串。

> [!NOTE]
> 如果清單方塊是一個下拉式清單方塊，則會將交換的值限制為255個字元。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_monthcalctrl"></a><a name="ddx_monthcalctrl"></a> DDX_MonthCalCtrl

此函式會 `DDX_MonthCalCtrl` 管理月曆控制項之間的日期資料傳輸 ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) 對話方塊、表單檢視或控制視圖物件中的) ，以及對話方塊、表單檢視或 control View 物件的 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 或 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 資料成員。

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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。 您不需要刪除此物件。

*nIDC*<br/>
與成員變數相關聯之月曆控制項的資源識別碼。

*value*<br/>
要 `CTime` `COleDateTime` 交換資料之對話方塊、表單檢視或 control view 物件的或成員變數參考。

### <a name="remarks"></a>備註

> [!NOTE]
> 控制項只會管理日期值。 時間物件中的時間欄位會設定為反映控制項視窗的建立時間，或在控制項中透過呼叫設定的任何時間 `CMonthCalCtrl::SetCurSel` 。

當 `DDX_MonthCalCtrl` 呼叫時， *值* 會設定為月曆控制項的目前狀態。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_radio"></a><a name="ddx_radio"></a> DDX_Radio

函式會 `DDX_Radio` 管理 **`int`** 對話方塊、表單檢視或控制項視圖物件中的選項按鈕控制項群組，以及 **`int`** 對話方塊、表單檢視或 control view 物件的資料成員之間的資料傳輸。 資料成員的值 **`int`** 會根據選取的群組中的選項按鈕來決定。

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
群組中第一個選項按鈕控制項的資源識別碼。

*value*<br/>
對話方塊的成員變數參考、表單檢視，或是用來交換資料的 control view 物件。

### <a name="remarks"></a>備註

當 `DDX_Radio` 呼叫時， *值* 會設定為選項按鈕控制項群組的目前狀態。 此值會設定為目前已選取之選項按鈕控制項以0為起始的索引; 如果未核取任何選項按鈕，則為-1。

例如，如果已檢查群組中的第一個選項按鈕 (具有 WS_GROUP 樣式的按鈕) 成員的值 **`int`** 為0，依此類推。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_scroll"></a><a name="ddx_scroll"></a> DDX_Scroll

函式會 `DDX_Scroll` 管理 **`int`** 對話方塊、表單檢視或控制項視圖物件中的捲軸控制項，以及 **`int`** 對話方塊、表單檢視或 control view 物件的資料成員之間的資料傳輸。

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
與控制項屬性相關聯之捲軸控制項的資源識別碼。

*value*<br/>
用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。

### <a name="remarks"></a>備註

當 `DDX_Scroll` 呼叫時， *值* 會設定為控制項 thumb 的目前位置。 如需與控制項 thumb 目前位置相關聯之值的詳細資訊，請參閱 Windows SDK 中的 [GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) 。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_slider"></a><a name="ddx_slider"></a> DDX_Slider

此函式會 `DDX_Slider` 管理 **`int`** 對話方塊或表單檢視中的滑杆控制項，以及 **`int`** 對話方塊或表單檢視物件的資料成員之間的資料傳輸。

```cpp
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
滑杆控制項的資源識別碼。

*value*<br/>
要交換之值的參考。 此參數會保存或設定滑杆控制項的目前位置。

### <a name="remarks"></a>備註

當 `DDX_Slider` 呼叫時， *值* 會設定為控制項 thumb 的目前位置，或根據交換的方向，將值接收到此位置。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需滑杆控制項的詳細資訊，請參閱 [使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="ddx_text"></a><a name="ddx_text"></a> DDX_Text

函 `DDX_Text` **`int`** 式會**UINT** **`long`** `CString` **`float`** **`double`** 在對話方塊、表單檢視或控制項視圖中的編輯控制項，以及對話方塊、表單檢視或 control view 物件的[CString](../../atl-mfc-shared/reference/cstringt-class.md)資料成員之間，管理、UINT、、DWORD、、或資料的傳輸。

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
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。

*nIDC*<br/>
對話方塊、表單檢視或 control view 物件中編輯控制項的識別碼。

*value*<br/>
對話方塊、表單檢視或 control view 物件中的資料成員參考。 *值*的資料類型取決於您所使用的多載版本 `DDX_Text` 。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdd_。h

## <a name="see-also"></a>另請參閱

[標準對話方塊資料驗證常式](standard-dialog-data-validation-routines.md)<br/>
[巨集和全域](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog：： OnInitDialog](cdialog-class.md#oninitdialog)
