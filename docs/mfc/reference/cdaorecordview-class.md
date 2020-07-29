---
title: CDaoRecordView 類別
ms.date: 11/04/2016
f1_keywords:
- CDaoRecordView
- AFXDAO/CDaoRecordView
- AFXDAO/CDaoRecordView::CDaoRecordView
- AFXDAO/CDaoRecordView::IsOnFirstRecord
- AFXDAO/CDaoRecordView::IsOnLastRecord
- AFXDAO/CDaoRecordView::OnGetRecordset
- AFXDAO/CDaoRecordView::OnMove
helpviewer_keywords:
- CDaoRecordView [MFC], CDaoRecordView
- CDaoRecordView [MFC], IsOnFirstRecord
- CDaoRecordView [MFC], IsOnLastRecord
- CDaoRecordView [MFC], OnGetRecordset
- CDaoRecordView [MFC], OnMove
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
ms.openlocfilehash: 95ed9207d0047287e373401da52f05235a817999
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223131"
---
# <a name="cdaorecordview-class"></a>CDaoRecordView 類別

在控制項中顯示資料庫記錄的檢視。

## <a name="syntax"></a>語法

```
class AFX_NOVTABLE CDaoRecordView : public CFormView
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|說明|
|----------|-----------------|
|[CDaoRecordView：： CDaoRecordView](#cdaorecordview)|建構 `CDaoRecordView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CDaoRecordView：： IsOnFirstRecord](#isonfirstrecord)|如果目前記錄是相關聯之記錄集內的第一筆記錄，則傳回非零。|
|[CDaoRecordView：： IsOnLastRecord](#isonlastrecord)|如果目前記錄是相關聯記錄集中的最後一筆記錄，則傳回非零。|
|[CDaoRecordView：： OnGetRecordset](#ongetrecordset)|傳回衍生自之類別物件的指標 `CDaoRecordset` 。 ClassWizard 會為您覆寫此函式，並在必要時建立記錄集。|
|[CDaoRecordView：： OnMove](#onmove)|如果目前的記錄已變更，會在資料來源上進行更新，然後移至指定的記錄（下一個、上一個、第一個或最後一個）。|

## <a name="remarks"></a>備註

View 是直接連接到物件的表單檢視 `CDaoRecordset` 。 此視圖會從對話方塊範本資源建立，並 `CDaoRecordset` 在對話方塊範本的控制項中顯示物件的欄位。 `CDaoRecordView`物件使用對話方塊資料交換（DDX）和 DAO 記錄欄位交換（DFX），在表單上的控制項與記錄集的欄位之間自動移動資料。 `CDaoRecordView`也提供移動到第一個、下一個、上一個或最後一筆記錄的預設執行，以及用來更新目前在 view 中記錄的介面。

> [!NOTE]
> DAO 資料庫類別與以開放式資料庫連接（ODBC）為基礎的 MFC 資料庫類別不同。 所有的 DAO 資料庫類別名稱都具有 "CDao" 前置詞。 您仍然可以使用 DAO 類別來存取 ODBC 資料來源。DAO 類別通常會提供卓越的功能，因為它們使用 Microsoft Jet 資料庫引擎。

建立記錄視圖最常見的方式是使用應用程式精靈。 應用程式精靈會同時建立記錄視圖類別及其相關聯的記錄集類別，做為您的基本架構入門應用程式的一部分。

如果您只需要單一表單，應用程式精靈的方法就比較容易。 ClassWizard 可讓您決定稍後在開發程式中使用記錄視圖。 如果您未使用應用程式精靈建立記錄視圖類別，您可以稍後使用 ClassWizard 加以建立。 使用 ClassWizard 來分別建立記錄視圖和記錄集，然後連接它們是最具彈性的方法，因為它可讓您更充分掌控記錄集類別及其的命名。H/。CPP 檔案。 這種方法也可讓您在相同的記錄集類別上擁有多個記錄 views。

為了讓使用者能夠輕鬆地在記錄視圖中從記錄移至記錄，應用程式精靈會建立可移至第一個、下一個、上一個或最後一個記錄的功能表（和選擇性的工具列）資源。 如果您使用 ClassWizard 建立記錄視圖類別，則需要使用功能表和點陣圖編輯器自行建立這些資源。

如需從記錄移至記錄的預設執行的詳細資訊，請參閱 `IsOnFirstRecord` 和 `IsOnLastRecord` 和[使用記錄視圖](../../data/using-a-record-view-mfc-data-access.md)的文章，這會同時套用至 `CRecordView` 和 `CDaoRecordView` 。

`CDaoRecordView`會追蹤使用者在記錄集中的位置，讓 [記錄] 視圖可以更新使用者介面。 當使用者移到記錄集的任一端時，記錄視圖會停用使用者介面物件（例如功能表項目或工具列按鈕），以便在相同的方向上進一步移動。

如需宣告和使用記錄視圖和記錄集類別的詳細資訊，請參閱[記錄 Views](../../data/record-views-mfc-data-access.md)一文中的「設計和建立記錄視圖」。 如需記錄查看的工作方式和使用方式的詳細資訊，請參閱[使用記錄視圖一](../../data/using-a-record-view-mfc-data-access.md)文。 以上所述的所有文章都適用于 `CRecordView` 和 `CDaoRecordView` 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CDaoRecordView`

## <a name="requirements"></a>需求

**標頭：** afxdao。h

## <a name="cdaorecordviewcdaorecordview"></a><a name="cdaorecordview"></a>CDaoRecordView：： CDaoRecordView

當您建立衍生自之類型的物件時 `CDaoRecordView` ，請呼叫任一形式的函式來初始化 view 物件，並識別此視圖所依據的對話資源。

```
explicit CDaoRecordView(LPCTSTR lpszTemplateName);
explicit CDaoRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>參數

*lpszTemplateName*<br/>
包含以 null 終止的字串，這是對話方塊範本資源的名稱。

*nIDTemplate*<br/>
包含對話方塊範本資源的 ID 編號。

### <a name="remarks"></a>備註

您可以依名稱（將字串當做引數傳遞至函式）或其識別碼（傳遞不帶正負號的整數做為引數）來識別資源。 建議使用資源識別碼。

> [!NOTE]
> 您的衍生類別必須提供自己的函數。 在衍生類別的函式中，呼叫 `CDaoRecordView::CDaoRecordView` 具有資源名稱或識別碼的函式做為引數。

`CDaoRecordView::OnInitialUpdate`呼叫 `CWnd::UpdateData` ，其會呼叫 `CWnd::DoDataExchange` 。 這個初始呼叫會 `DoDataExchange` 將 `CDaoRecordView` 控制項（間接）連接到 `CDaoRecordset` ClassWizard 所建立的欄位資料成員。 在您呼叫基類成員函式之前，不能使用這些資料成員 `CFormView::OnInitialUpdate` 。

> [!NOTE]
> 如果您使用 ClassWizard，則 wizard 會定義 **`enum`** 類別宣告中的值 `CDaoRecordView::IDD` ，並在此函式的成員初始化清單中使用它。

[!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]

## <a name="cdaorecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CDaoRecordView：： IsOnFirstRecord

呼叫這個成員函式，以判斷目前的記錄是否為記錄集物件中與此記錄視圖相關聯的第一筆記錄。

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>傳回值

如果目前記錄是記錄集內的第一筆記錄，則為非零。否則為0。

### <a name="remarks"></a>備註

此函式適用于撰寫您自己的 ClassWizard 所撰寫的預設命令更新處理常式的執行。

如果使用者移至第一筆記錄，則架構會停用您移至第一個或上一個記錄所需的任何使用者介面物件（例如功能表項目或工具列按鈕）。

## <a name="cdaorecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CDaoRecordView：： IsOnLastRecord

呼叫這個成員函式，以判斷目前的記錄是否為與此記錄視圖相關聯之記錄集物件中的最後一筆記錄。

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>傳回值

如果目前記錄是記錄集內的最後一筆記錄，則為非零。否則為0。

### <a name="remarks"></a>備註

此函式可用於撰寫您自己的預設命令更新處理常式的執行，以 ClassWizard 寫入以支援從記錄移至記錄的使用者介面。

> [!CAUTION]
> 此函式的結果是可靠的，不同之處在于此視圖可能無法偵測記錄集的結尾，直到使用者移動過它為止。 使用者可能必須先移至最後一筆記錄之後，記錄視圖才會告訴它必須停用任何使用者介面物件，以移至下一個或最後一筆記錄。 如果使用者在最後一筆記錄之後移動，然後回到最後一筆記錄（或之前），則記錄視圖可以追蹤使用者在記錄集中的位置，並正確地停用使用者介面物件。

## <a name="cdaorecordviewongetrecordset"></a><a name="ongetrecordset"></a>CDaoRecordView：： OnGetRecordset

傳回 `CDaoRecordset` 與記錄視圖相關聯之衍生物件的指標。

```
virtual CDaoRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>傳回值

`CDaoRecordset`如果成功建立物件，則為衍生物件的指標; 否則為 Null 指標。

### <a name="remarks"></a>備註

您必須覆寫這個成員函式，才能建立或取得記錄集物件，並傳回它的指標。 如果您使用 ClassWizard 宣告您的記錄視圖類別，則 wizard 會為您撰寫預設覆寫。 ClassWizard 的預設實值會傳回記錄視圖中儲存的記錄集指標（如果有的話）。 如果不是，它會針對您使用 ClassWizard 所指定的類型來建立記錄集物件，並呼叫其成員函式 `Open` 來開啟資料表或執行查詢，然後傳回物件的指標。

如需詳細資訊和範例，請參閱[記錄 Views：使用記錄視圖一](../../data/using-a-record-view-mfc-data-access.md)文。

## <a name="cdaorecordviewonmove"></a><a name="onmove"></a>CDaoRecordView：： OnMove

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

預設的執行會呼叫 `CDaoRecordset` 與記錄視圖相關聯之物件的適當移動成員函式。

根據預設， `OnMove` 如果使用者已在 [記錄] 視圖中變更資料來源上的目前記錄，則會進行更新。

應用程式精靈會建立具有第一筆記錄、最後記錄、下一筆記錄，以及上一個 [記錄] 功能表項目的功能表資源。 如果您選取 [初始] 工具列選項，應用程式精靈也會建立一個工具列，其中包含與這些命令對應的按鈕。

如果您移動記錄集內的最後一筆記錄，記錄視圖會繼續顯示最後一筆記錄。 如果您在第一筆記錄之後移動，記錄視圖會繼續顯示第一筆記錄。

> [!CAUTION]
> `OnMove`如果記錄集沒有任何記錄，則呼叫會擲回例外狀況。 在對應的移動作業之前，呼叫適當的使用者介面更新處理常式函式（ `OnUpdateRecordFirst` 、 `OnUpdateRecordLast` 、 `OnUpdateRecordNext` 或 `OnUpdateRecordPrev` ），以判斷記錄集是否有任何記錄。

## <a name="see-also"></a>另請參閱

[CFormView 類別](../../mfc/reference/cformview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoWorkspace 類別](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CFormView 類別](../../mfc/reference/cformview-class.md)
