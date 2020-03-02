---
title: CRecordView 類別
ms.date: 11/04/2016
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
ms.openlocfilehash: 409739d97c9f7ae9a730ac8f05bd86e647da2c71
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215538"
---
# <a name="crecordview-class"></a>CRecordView 類別

在控制項中顯示資料庫記錄的檢視。

## <a name="syntax"></a>語法

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CRecordView：： CRecordView](#crecordview)|建構 `CRecordView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRecordView：： IsOnFirstRecord](#isonfirstrecord)|如果目前記錄是相關聯之記錄集內的第一筆記錄，則傳回非零。|
|[CRecordView：： IsOnLastRecord](#isonlastrecord)|如果目前記錄是相關聯記錄集中的最後一筆記錄，則傳回非零。|
|[CRecordView：： OnGetRecordset](#ongetrecordset)|傳回衍生自 `CRecordset`之類別的物件指標。 ClassWizard 會為您覆寫此函式，並在必要時建立記錄集。|
|[CRecordView：： OnMove](#onmove)||

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[CRecordView：： OnMove](#onmove)|如果目前的記錄已變更，會在資料來源上進行更新，然後移至指定的記錄（下一個、上一個、第一個或最後一個）。|

## <a name="remarks"></a>備註

View 是直接連接到 `CRecordset` 物件的表單檢視。 此視圖會從對話方塊範本資源建立，並在對話方塊範本的控制項中顯示 `CRecordset` 物件的欄位。 `CRecordView` 物件使用對話方塊資料交換（DDX）和記錄欄位交換（RFX），將表單上的控制項與記錄集的欄位之間的資料移動自動化。 `CRecordView` 也會提供移動到第一個、下一個、上一個或最後一個記錄的預設執行，以及用來更新目前在 view 上之記錄的介面。

> [!NOTE]
>  如果您使用的是資料存取物件（DAO）類別，而不是開放式資料庫連接（ODBC）類別，請改用 [類別[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) ]。 如需詳細資訊，請參閱文章[總覽：資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

建立記錄視圖最常見的方式是使用應用程式精靈。 應用程式精靈會同時建立記錄視圖類別及其相關聯的記錄集類別，做為您的基本架構入門應用程式的一部分。 如果您未使用應用程式精靈建立記錄視圖類別，您可以稍後使用 ClassWizard 加以建立。 如果您只需要單一表單，應用程式精靈的方法就比較容易。 ClassWizard 可讓您決定稍後在開發程式中使用記錄視圖。 使用 ClassWizard 來分別建立記錄視圖和記錄集，然後連接它們是最具彈性的方法，因為它可讓您更充分掌控記錄集類別及其的命名。H/。CPP 檔案。 這種方法也可讓您在相同的記錄集類別上擁有多個記錄 views。

為了讓使用者能夠輕鬆地在記錄視圖中從記錄移至記錄，應用程式精靈會建立可移至第一個、下一個、上一個或最後一個記錄的功能表（和選擇性的工具列）資源。 如果您使用 ClassWizard 建立記錄視圖類別，則需要使用功能表和點陣圖編輯器自行建立這些資源。

如需從記錄移至記錄的預設執行的詳細資訊，請參閱 `IsOnFirstRecord` 和 `IsOnLastRecord` 和[使用記錄視圖](../../data/using-a-record-view-mfc-data-access.md)的文章。

`CRecordView` 會追蹤使用者在記錄集中的位置，以便讓 [記錄] 視圖可以更新使用者介面。 當使用者移到記錄集的任一端時，記錄視圖會停用使用者介面物件（例如功能表項目或工具列按鈕），以便在相同的方向上進一步移動。

如需宣告和使用記錄視圖和記錄集類別的詳細資訊，請參閱[記錄 Views](../../data/record-views-mfc-data-access.md)一文中的「設計和建立記錄視圖」。 如需記錄查看的工作方式和使用方式的詳細資訊，請參閱[使用記錄視圖一](../../data/using-a-record-view-mfc-data-access.md)文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>需求

**標頭：** afxdb。h

##  <a name="crecordview"></a>CRecordView：： CRecordView

當您建立衍生自 `CRecordView`之類型的物件時，請呼叫任一形式的函式來初始化 view 物件，並識別此視圖所依據的對話資源。

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>參數

*lpszTemplateName*<br/>
包含以 null 終止的字串，這是對話方塊範本資源的名稱。

*nIDTemplate*<br/>
包含對話方塊範本資源的 ID 編號。

### <a name="remarks"></a>備註

您可以依名稱（將字串當做引數傳遞至函式）或其識別碼（傳遞不帶正負號的整數做為引數）來識別資源。 建議使用資源識別碼。

> [!NOTE]
>  您的衍生類別*必須*提供自己的函數。 在衍生類別的函式中，呼叫具有資源名稱或識別碼的 `CRecordView::CRecordView` 的函式做為引數，如下列範例所示。

`CRecordView::OnInitialUpdate` 呼叫 `UpdateData`，這會呼叫 `DoDataExchange`。 這項初始呼叫 `DoDataExchange` 會將 `CRecordView` 控制項（間接）連接到 ClassWizard 所建立的 `CRecordset` 欄位資料成員。 在您呼叫基類 `CFormView::OnInitialUpdate` 成員函式之前，都無法使用這些資料成員。

> [!NOTE]
>  如果您使用 ClassWizard，則 wizard 會定義**列舉**值 `CRecordView::IDD`、在類別宣告中指定它，並在此函式的成員初始化清單中使用它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

##  <a name="isonfirstrecord"></a>CRecordView：： IsOnFirstRecord

呼叫這個成員函式，以判斷目前的記錄是否為記錄集物件中與此記錄視圖相關聯的第一筆記錄。

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>傳回值

如果目前記錄是記錄集內的第一筆記錄，則為非零。否則為0。

### <a name="remarks"></a>備註

此函式適用于撰寫您自己的預設命令更新處理常式（由 ClassWizard 所撰寫）的執行。

如果使用者移至第一筆記錄，則架構會停用您要移至第一個或上一個記錄的任何使用者介面物件。

##  <a name="isonlastrecord"></a>CRecordView：： IsOnLastRecord

呼叫這個成員函式，以判斷目前的記錄是否為與此記錄視圖相關聯之記錄集物件中的最後一筆記錄。

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>傳回值

如果目前記錄是記錄集內的最後一筆記錄，則為非零。否則為0。

### <a name="remarks"></a>備註

此函式可用於撰寫您自己的預設命令更新處理常式的執行，以 ClassWizard 寫入以支援從記錄移至記錄的使用者介面。

> [!CAUTION]
>  此函式的結果是可靠的，不同之處在于此視圖無法偵測記錄集的結尾，直到使用者將其移到過去為止。 使用者必須移至最後一筆記錄之後，記錄視圖才會告訴它必須停用任何使用者介面物件，以移至下一個或最後一筆記錄。 如果使用者在最後一筆記錄之後移動，然後回到最後一筆記錄（或之前），則記錄視圖可以追蹤使用者在記錄集中的位置，並正確地停用使用者介面物件。 在呼叫實函式 `OnRecordLast`（處理 ID_RECORD_LAST 命令或 `CRecordset::MoveLast`）之後，`IsOnLastRecord` 也不可靠。

##  <a name="ongetrecordset"></a>CRecordView：： OnGetRecordset

傳回與記錄視圖相關聯之 `CRecordset`衍生物件的指標。

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>傳回值

如果成功建立物件，則為 `CRecordset`衍生物件的指標;否則為 Null 指標。

### <a name="remarks"></a>備註

您必須覆寫這個成員函式，才能建立或取得記錄集物件，並傳回它的指標。 如果您使用 ClassWizard 宣告您的記錄視圖類別，則 wizard 會為您撰寫預設覆寫。 ClassWizard 的預設實值會傳回記錄視圖中儲存的記錄集指標（如果有的話）。 如果不是，它會使用 ClassWizard 來建立您指定之類型的記錄集物件，並呼叫其 `Open` 成員函式來開啟資料表或執行查詢，然後傳回物件的指標。

如需詳細資訊和範例，請參閱[記錄 Views：使用記錄視圖一](../../data/using-a-record-view-mfc-data-access.md)文。

##  <a name="onmove"></a>CRecordView：： OnMove

呼叫這個成員函式可移至記錄集中的不同記錄，並在記錄視圖的控制項中顯示其欄位。

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>參數

*nIDMoveCommand*<br/>
下列其中一個標準命令識別碼值：

- ID_RECORD_FIRST 移至記錄集內的第一筆記錄。

- ID_RECORD_LAST 移至記錄集的最後一筆記錄。

- ID_RECORD_NEXT 移至記錄集中的下一筆記錄。

- ID_RECORD_PREV 移至記錄集內的上一個記錄。

### <a name="return-value"></a>傳回值

如果移動成功，則為非零;如果移動要求遭到拒絕，則為0。

### <a name="remarks"></a>備註

預設的執行會呼叫與記錄視圖相關聯之 `CRecordset` 物件的適當 `Move` 成員函式。

根據預設，如果使用者已在 [記錄] 視圖中變更資料來源上的目前記錄，`OnMove` 會將其更新。

應用程式精靈會建立具有第一筆記錄、最後記錄、下一筆記錄，以及上一個 [記錄] 功能表項目的功能表資源。 如果您選取 [可停駐的工具列] 選項，應用程式精靈也會建立一個工具列，其中包含與這些命令對應的按鈕。

如果您移動記錄集內的最後一筆記錄，記錄視圖會繼續顯示最後一筆記錄。 如果您在第一筆記錄之後移動，記錄視圖會繼續顯示第一筆記錄。

> [!CAUTION]
>  如果記錄集沒有任何記錄，則呼叫 `OnMove` 會擲回例外狀況。 在對應的移動作業之前，呼叫適當的使用者介面更新處理常式函式（`OnUpdateRecordFirst`、`OnUpdateRecordLast`、`OnUpdateRecordNext`或 `OnUpdateRecordPrev`），以判斷記錄集是否有任何記錄。

## <a name="see-also"></a>另請參閱

[CFormView 類別](../../mfc/reference/cformview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)<br/>
[CFormView 類別](../../mfc/reference/cformview-class.md)
