---
title: 標準對話方塊資料交換常式
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 47586f9cff0fcbe2cd7bad31f3d93fed08190830
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511577"
---
# <a name="standard-dialog-data-exchange-routines"></a>標準對話方塊資料交換常式

本主題列出常用 MFC 對話方塊控制項所使用的標準對話資料交換（DDX）常式。

> [!NOTE]
>  標準對話方塊資料交換常式會定義在標頭檔 afxdd_ 中。 不過，應用程式應該包含 afxwin.h。

### <a name="ddx-functions"></a>DDX 函式

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|初始化或抓取下拉式方塊控制項目前選取範圍的索引。|
|[DDX_CBString](#ddx_cbstring)|初始化或抓取下拉式方塊控制項之編輯欄位的目前內容。|
|[DDX_CBStringExact](#ddx_cbstringexact)|初始化或抓取下拉式方塊控制項之編輯欄位的目前內容。|
|[DDX_Check](#ddx_check)|初始化或抓取核取方塊控制項的目前狀態。|
|[DDX_Control](#ddx_control)|子類別化對話方塊中的指定控制項。|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|初始化或抓取日期和時間選擇器控制項的日期和/或時間資料。|
|[DDX_IPAddress](#ddx_ipaddress)|初始化或抓取 IP 位址控制項的目前值。|
|[DDX_LBIndex](#ddx_lbindex)|初始化或抓取清單方塊控制項目前選取範圍的索引。|
|[DDX_LBString](#ddx_lbstring)|初始化或抓取清單方塊控制項中目前的選取範圍。|
|[DDX_LBStringExact](#ddx_lbstringexact)|初始化或抓取清單方塊控制項中目前的選取範圍。|
|[DDX_ManagedControl](#ddx_managedcontrol)|建立符合控制項資源識別碼的 .NET 控制項。|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|初始化或抓取月曆控制項的目前值。|
|[DDX_Radio](#ddx_radio)|初始化或抓取目前在選項按鈕控制項群組內檢查之選項按鈕控制項的以零為起始的索引。|
|[DDX_Scroll](#ddx_scroll)|初始化或抓取捲軸控制項捲動方塊的目前位置。|
|[DDX_Slider](#ddx_slider)|初始化或抓取滑杆控制項捲動方塊的目前位置。|
|[DDX_Text](#ddx_text)|初始化或抓取編輯控制項的目前值。|

##  <a name="ddx_cbindex"></a>  DDX_CBIndex

函式會管理對話方塊、表單檢視或控制項視圖物件中下拉式方塊控制項與對話方塊、表單檢視或控制項視圖物件之**int**資料成員之間的 int 資料傳輸。 `DDX_CBIndex`

```
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
與交換資料的對話方塊、表單檢視或控制項視圖物件之成員變數的參考。

### <a name="remarks"></a>備註

當`DDX_CBIndex`呼叫時， *index*會設定為目前下拉式列示方塊選取專案的索引。 如果未選取任何專案，則*index*會設定為0。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

##  <a name="ddx_cbstring"></a>DDX_CBString

函式會管理對話方塊、 `CString`表單檢視或`CString`控制項視圖物件中下拉式方塊控制項的編輯控制項與對話方塊、表單檢視或控制項視圖物件的資料成員之間的資料傳輸。 `DDX_CBString`

```
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
與交換資料的對話方塊、表單檢視或控制項視圖物件之成員變數的參考。

### <a name="remarks"></a>備註

當`DDX_CBString`呼叫時，[*值*] 會設定為目前的下拉式列示方塊選取專案。 如果未選取任何專案，則 [*值*] 會設定為長度為零的字串。

> [!NOTE]
>  如果下拉式方塊是下拉式清單方塊，則交換的值會限制為255個字元。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

##  <a name="ddx_cbstringexact"></a>  DDX_CBStringExact

函式會管理對話方塊、 `CString`表單檢視或`CString`控制項視圖物件中下拉式方塊控制項的編輯控制項與對話方塊、表單檢視或控制項視圖物件的資料成員之間的資料傳輸。 `DDX_CBStringExact`

```
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
與交換資料的對話方塊、表單檢視或控制項視圖物件之成員變數的參考。

### <a name="remarks"></a>備註

當`DDX_CBStringExact`呼叫時，[*值*] 會設定為目前的下拉式列示方塊選取專案。 如果未選取任何專案，則 [*值*] 會設定為長度為零的字串。

> [!NOTE]
>  如果下拉式方塊是下拉式清單方塊，則交換的值會限制為255個字元。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

##  <a name="ddx_check"></a>  DDX_Check

函式會管理對話方塊、表單檢視或控制項視圖物件中核取方塊控制項與對話方塊、表單檢視或控制項視圖物件之**int**資料成員之間的 int 資料傳輸。 `DDX_Check`

```
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
與交換資料的對話方塊、表單檢視或控制項視圖物件之成員變數的參考。

### <a name="remarks"></a>備註

當`DDX_Check`呼叫時，[*值*] 會設定為核取方塊控制項的目前狀態。 如需可能狀態值的清單，請參閱 Windows SDK 中的[BM_GETCHECK](/windows/win32/Controls/bm-getcheck) 。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

##  <a name="ddx_control"></a>  DDX_Control

函式會子類別化對話方塊、表單檢視或控制項視圖物件的 nIDC 所指定的控制項。 `DDX_Control`

```
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
與指定控制項相關之對話方塊、表單檢視或控制項視圖物件之成員變數的參考。

### <a name="remarks"></a>備註

呼叫 `DoDataExchange`函數時，架構會提供 pDX 物件。 因此， `DDX_Control`應該只在的`DoDataExchange`覆寫內呼叫。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

##  <a name="ddx_datetimectrl"></a>  DDX_DateTimeCtrl

函式會管理對話方塊或表單檢視物件中日期和時間選擇器控制項（[CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)）與對話方塊或表單的 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 或 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 資料成員之間的日期和（或）時間資料傳輸 `DDX_DateTimeCtrl`view 物件。

```
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
在前兩個版本中，是用來`CTime`交換`COleDateTime`資料的或成員變數、對話方塊、表單檢視或控制項視圖物件的參考。 在第三個版本中，是`CString`資料成員控制項 view 物件的參考。

### <a name="remarks"></a>備註

當`DDX_DateTimeCtrl`呼叫時，[*值*] 會設定為 [日期和時間選擇器] 控制項的目前狀態，或 [控制項] 設定為 [*值*] （視交換的方向而定）。

在上述的第三個`DDX_DateTimeCtrl`版本中，會`CString`管理日期時間控制項與 control view 物件的[CString](../../atl-mfc-shared/reference/cstringt-class.md)資料成員之間的資料傳輸。 字串會使用目前地區設定的日期和時間格式規則來格式化。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="ddx_managedcontrol"></a>DDX_ManagedControl

建立符合控制項資源識別碼的 .NET 控制項。

### <a name="syntax"></a>語法

```
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

`DDX_ManagedControl`呼叫[CWinFormsControl：： CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)來建立符合資源控制識別碼的控制項。 使用`DDX_ManagedControl`可從[CDialog：： OnInitDialog](cdialog-class.md#oninitdialog)中的資源識別碼建立控制項。 對於資料交換，您不需要搭配 Windows Forms 控制項使用 DDX/DDV 函式。

如需詳細資訊，請參閱[如何：使用 Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)執行 DDX/DDV 資料系結。

### <a name="requirements"></a>需求

**標頭：** afxwinforms。h

##  <a name="ddx_ipaddress"></a>  DDX_IPAddress

此`DDX_IPAddress`函式會管理 IP 位址控制項與 control view 物件的資料成員之間的資料傳輸。

```
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
DWORD 的參考，其中包含 IP 位址控制項的四個域值。 欄位會填入或閱讀，如下所示。

|欄位|包含域值的位|
|-----------|-------------------------------------|
|3|0到7|
|2|8至15|
|1|16到23|
|0|24到31|

使用 Win32 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress)來讀取值，或使用[IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)來填滿值。 Windows SDK 中會描述這些訊息。

### <a name="remarks"></a>備註

當`DDX_IPAddress`呼叫時，會從 IP 位址控制讀取*值*，或將*值*寫入至控制項（視交換的方向而定）。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

##  <a name="ddx_lbindex"></a>  DDX_LBIndex

函式會管理對話方塊、表單檢視或控制項視圖物件中清單方塊控制項與對話方塊、表單檢視或控制項視圖物件之**int**資料成員之間的 int 資料傳輸。 `DDX_LBIndex`

```
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
與交換資料的對話方塊、表單檢視或控制項視圖物件之成員變數的參考。

### <a name="remarks"></a>備註

當`DDX_LBIndex`呼叫時， *index*會設定為目前清單方塊選取範圍的索引。 如果未選取任何專案，則*index*會設定為-1。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

##  <a name="ddx_lbstring"></a>  DDX_LBString

函式會管理對話方塊、 `CString`表單檢視或`CString`控制項視圖物件中清單方塊控制項與對話方塊、表單檢視或控制項視圖物件之資料成員之間的資料傳輸。 `DDX_LBString`

```
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
與交換資料的對話方塊、表單檢視或控制項視圖物件之成員變數的參考。

### <a name="remarks"></a>備註

呼叫`DDX_LBString`以將資料傳送至清單方塊控制項時，會選取控制項中的第一個專案，其開頭符合*值*為。 （若要比對整個專案，而不只是前置詞，請使用[DDX_LBStringExact](#ddx_lbstringexact)）。如果沒有相符專案，則不會選取任何專案。 比對不區分大小寫。

呼叫`DDX_LBString`以從清單方塊控制項傳送資料時，*值*會設定為目前的清單方塊選取專案。 如果未選取任何專案，則 [*值*] 會設定為長度為零的字串。

> [!NOTE]
>  如果清單方塊是下拉式清單方塊，則會將交換的值限制為255個字元。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

##  <a name="ddx_lbstringexact"></a>  DDX_LBStringExact

函式會管理對話方塊、 `CString`表單檢視或`CString`控制項視圖物件中清單方塊控制項的編輯控制項與對話方塊、表單檢視或控制項視圖物件的資料成員之間的資料傳輸。 `DDX_CBStringExact`

```
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
與交換資料的對話方塊、表單檢視或控制項視圖物件之成員變數的參考。

### <a name="remarks"></a>備註

呼叫`DDX_LBStringExact`以將資料傳送至清單方塊控制項時，會選取符合 [*值*] 之控制項中的第一個專案。 （若只要比對前置詞，而不是整個專案，請使用[DDX_LBString](#ddx_lbstring)）。如果沒有相符專案，則不會選取任何專案。 比對不區分大小寫。

呼叫`DDX_CBStringExact`以從清單方塊控制項傳送資料時，*值*會設定為目前的清單方塊選取專案。 如果未選取任何專案，則 [*值*] 會設定為長度為零的字串。

> [!NOTE]
>  如果清單方塊是下拉式清單方塊，則會將交換的值限制為255個字元。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

##  <a name="ddx_monthcalctrl"></a>  DDX_MonthCalCtrl

函式會管理對話方塊、表單檢視或控制項視圖物件中月曆控制項（ [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)）之間的日期資料傳輸，以及對話方塊的[CTime](../../atl-mfc-shared/reference/ctime-class.md)或 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 資料成員，表單 `DDX_MonthCalCtrl`view 或 control view 物件。

```
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
與交換資料的`CTime`對話方塊`COleDateTime` 、表單檢視或控制項視圖物件之或成員變數的參考。

### <a name="remarks"></a>備註

> [!NOTE]
>  控制項只會管理日期值。 時間物件中的時間欄位會設定為反映控制項視窗的建立時間，或在控制項中使用呼叫`CMonthCalCtrl::SetCurSel`所設定的任何時間。

當`DDX_MonthCalCtrl`呼叫時，[*值*] 會設定為月曆控制項的目前狀態。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

##  <a name="ddx_radio"></a>DDX_Radio

函式會管理對話方塊、表單檢視或控制項視圖物件中的選項按鈕控制項群組與對話方塊、表單檢視或控制項視圖物件的**int**資料成員之間的 int 資料傳輸。 `DDX_Radio` **Int**資料成員的值是根據群組內所選取的選項按鈕來決定。

```
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
與交換資料的對話方塊、表單檢視或控制項視圖物件之成員變數的參考。

### <a name="remarks"></a>備註

當`DDX_Radio`呼叫時，*值*會設定為選項按鈕控制項群組的目前狀態。 此值會設定為目前所選取之選項按鈕控制項的以零為起始的索引，如果未核取任何選項按鈕，則設為-1。

例如，如果已核取群組中的第一個選項按鈕（具有 WS_GROUP 樣式的按鈕），則**int**成員的值為0，依此類推。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

##  <a name="ddx_scroll"></a>  DDX_Scroll

函式會管理對話方塊、表單檢視或控制項視圖物件中的捲軸控制項與對話方塊、表單檢視或控制項視圖物件的**int**資料成員之間的 int 資料傳輸。 `DDX_Scroll`

```
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

當`DDX_Scroll`呼叫時，*值*會設定為控制項捲動方塊的目前位置。 如需與控制項的目前位置相關聯之值的詳細資訊，請參閱 Windows SDK 中的[GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) 。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

##  <a name="ddx_slider"></a>  DDX_Slider

函式會管理對話方塊或表單檢視中的滑杆控制項與對話方塊或表單檢視物件的**int**資料成員之間的 int 資料傳輸。 `DDX_Slider`

```
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
要交換之值的參考。 這個參數會保留或設定滑杆控制項的目前位置。

### <a name="remarks"></a>備註

當`DDX_Slider`呼叫時，[*值*] 會設定為控制項捲動方塊的目前位置，或值會接收位置，視交換的方向而定。

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需滑杆控制項的相關資訊，請參閱[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

##  <a name="ddx_text"></a>DDX_Text

函式會管理對話方塊、表單檢視或控制項視圖和 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 資料中編輯控制項之間的 **int**、**UINT**、**long**、DWORD`CString`、float 或 double 資料傳輸`DDX_Text`對話方塊、表單檢視或控制項視圖物件的成員。

```
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
對話方塊、表單檢視或控制項視圖物件中編輯控制項的識別碼。

*value*<br/>
對話方塊、表單檢視或控制項視圖物件中之資料成員的參考。 *值*的資料類型取決於`DDX_Text`您所使用的多載版本。

### <a name="remarks"></a>備註

如需有關 DDX 的詳細資訊，請參閱 [對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>需求

  **標頭**afxdd_。h

## <a name="see-also"></a>另請參閱

[標準對話方塊資料驗證常式](standard-dialog-data-validation-routines.md)<br/>
[宏和全域](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
