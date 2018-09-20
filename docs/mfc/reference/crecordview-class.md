---
title: CRecordView 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
dev_langs:
- C++
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23d756afd790fde4ad3bda5519a35901e043860f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432837"
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
|[CRecordView::CRecordView](#crecordview)|建構 `CRecordView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|傳回非零值，如果目前的記錄中相關聯的資料錄集的第一筆記錄。|
|[CRecordView::IsOnLastRecord](#isonlastrecord)|傳回非零值，如果目前的記錄相關聯的資料錄集中的最後一筆記錄。|
|[CRecordView::OnGetRecordset](#ongetrecordset)|傳回衍生自類別的物件的指標`CRecordset`。 ClassWizard 覆寫這個函式，為您，並在必要時建立資料錄集。|
|[CRecordView::OnMove](#onmove)||

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CRecordView::OnMove](#onmove)|如果目前資料錄已變更，更新資料來源上，則會移至指定的記錄 （下一步、 上一個，第一個或最後一個）。|

## <a name="remarks"></a>備註

檢視是表單檢視，直接連線到`CRecordset`物件。 檢視從對話方塊範本資源建立，並顯示的欄位`CRecordset`對話方塊範本的控制項中的物件。 `CRecordView`物件用來自動化的表單上的控制項和資料錄集的欄位之間的資料移動的對話方塊資料交換 (DDX) 和資料錄欄位交換 (RFX)。 `CRecordView` 也提供移動的預設實作第一筆、 下一步 上, 一個或最後一筆和更新目前的檢視記錄的介面。

> [!NOTE]
>  如果您正在使用的資料存取物件 (DAO) 類別，而不是開放式資料庫連接 (ODBC) 類別，使用類別[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)改。 如需詳細資訊，請參閱文章[概觀： 資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

若要建立您的資料錄檢視的最常見方式是使用應用程式精靈。 Tge 應用程式精靈 建立資料錄檢視類別和其相關聯的資料錄集類別，做為您的基本架構的入門應用程式的一部分。 如果您未建立資料錄檢視類別與應用程式精靈，可以使用 ClassWizard 稍後建立它。 如果您只需要單一的表單時，應用程式精靈 的方法是更容易。 ClassWizard 可讓您決定使用資料錄檢視稍後在開發程序。 分別建立資料錄檢視和資料錄集，然後將它們連接至使用 ClassWizard 是最具彈性的方法，因為它讓您更能控制中命名的資料錄集類別和其。H /。CPP 檔案。 這種方法也可讓您有多個資料錄檢視上相同的資料錄集類別。

為了方便使用者記錄從移動資料錄檢視中，應用程式精靈會建立功能表 （及選擇性地工具列） 資源移動第一筆、 下一步 上, 一個或最後一筆記錄。 如果您建立資料錄檢視類別與 ClassWizard 時，您需要這些資源自行建立具有功能表和點陣圖編輯器。

移動記錄間的預設實作的相關資訊，請參閱`IsOnFirstRecord`並`IsOnLastRecord`和 發行項[使用資料錄檢視](../../data/using-a-record-view-mfc-data-access.md)。

`CRecordView` 會追蹤的資料錄集的使用者的位置，以便資料錄檢視可以更新使用者介面。 當使用者移至任一端的資料錄集時，資料錄檢視停用使用者介面物件，例如功能表項目或工具列按鈕 — 移動中相同的方向。

多個宣告和使用您的資料錄檢視和資料錄集類別的詳細資訊，請參閱 「 設計和建立資料錄檢視 >，文件中[資料錄檢視](../../data/record-views-mfc-data-access.md)。 如需有關資料錄檢視工作的方式，以及如何使用它們的詳細資訊，請參閱[使用資料錄檢視](../../data/using-a-record-view-mfc-data-access.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>需求

**標頭：** afxdb.h

##  <a name="crecordview"></a>  CRecordView::CRecordView

當您建立的物件型別的衍生自`CRecordView`，呼叫建構函式來初始化檢視的物件，並識別對話方塊資源檢視所依據的任一形式。

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>參數

*lpszTemplateName*<br/>
包含 null 結束的字串，這是對話方塊範本資源的名稱。

*nIDTemplate*<br/>
包含對話方塊範本資源的識別碼。

### <a name="remarks"></a>備註

依名稱 (pass 字串做為引數的建構函式) 或其識別碼 (pass 不帶正負號的整數做為引數)，您可能可以識別資源。 資源識別碼，建議使用。

> [!NOTE]
>  您的衍生的類別*必須*提供它自己的建構函式。 在衍生類別的建構函式，呼叫建構函式`CRecordView::CRecordView`資源名稱或識別碼做為引數，如下列範例所示。

`CRecordView::OnInitialUpdate` 呼叫`UpdateData`，其會呼叫`DoDataExchange`。 這次呼叫`DoDataExchange`連接`CRecordView`（間接） 為控制`CRecordset`欄位 ClassWizard 所建立的資料成員。 這些資料成員無法使用之前之後您呼叫的基底類別,`CFormView::OnInitialUpdate`成員函式。

> [!NOTE]
>  如果您使用 ClassWizard，精靈會定義**enum**值`CRecordView::IDD`、 在類別宣告中，指定它，並建構函式使用成員初始設定清單中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

##  <a name="isonfirstrecord"></a>  CRecordView::IsOnFirstRecord

呼叫此成員函式，以判斷目前的記錄是否與此資料錄檢視相關聯之資料錄集物件中的第一筆記錄。

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>傳回值

如果目前的記錄資料錄集; 第一筆記錄，非零值。否則為 0。

### <a name="remarks"></a>備註

此函式可用於撰寫您自己的預設實作 ClassWizard 所撰寫的命令更新處理常式。

如果使用者移至第一筆記錄，架構會停用您移至第一個或前一筆記錄有任何使用者介面物件。

##  <a name="isonlastrecord"></a>  CRecordView::IsOnLastRecord

呼叫此成員函式，以判斷目前的記錄是否與此資料錄檢視相關聯之資料錄集物件中的最後一筆記錄。

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>傳回值

如果目前的記錄資料錄集; 最後一筆記錄，非零值。否則為 0。

### <a name="remarks"></a>備註

此函式可用於撰寫您自己的預設實作 ClassWizard 寫入移轉記錄間支援的使用者介面的命令更新處理常式。

> [!CAUTION]
>  此函式的結果是可靠的不同之處在於檢視無法偵測到資料錄集的結尾，直到使用者已移動過。 資料錄檢視所見，它必須停用將移至下一個或最後一筆記錄的任何使用者介面物件之前，使用者必須移動超過最後一筆記錄。 如果使用者移至將最後一筆記錄，然後移回至最後一個記錄 （或之前），資料錄檢視可以追蹤使用者的資料錄集中的位置，並正確地停用使用者介面物件。 `IsOnLastRecord` 實作函式的呼叫之後也不可靠`OnRecordLast`，處理 ID_RECORD_LAST 命令，或`CRecordset::MoveLast`。

##  <a name="ongetrecordset"></a>  CRecordView::OnGetRecordset

將指標傳回至`CRecordset`-衍生的資料錄檢視相關聯的物件。

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>傳回值

指標`CRecordset`-衍生物件，如果物件已成功建立，否則為 NULL 指標。

### <a name="remarks"></a>備註

您必須覆寫此成員函式，來建構或取得資料錄集物件和傳回的指標。 如果您宣告您的資料錄檢視類別與 ClassWizard，精靈會為您撰寫的預設覆寫。 ClassWizard 的預設實作會傳回資料錄集指標儲存在記錄檢視中，如果有的話。 您如果不是，它會建構類型的資料錄集物件指定 ClassWizard 並呼叫其`Open`成員函式以開啟資料表或執行查詢，並再傳回物件的指標。

如需詳細資訊和範例，請參閱文章[資料錄檢視： 使用資料錄檢視](../../data/using-a-record-view-mfc-data-access.md)。

##  <a name="onmove"></a>  CRecordView::OnMove

呼叫此成員函式，將移至不同的記錄資料錄集，顯示其欄位的資料錄檢視控制項中。

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>參數

*nIDMoveCommand*<br/>
其中一個下列的標準命令 ID 值：

- ID_RECORD_FIRST 將移至資料錄集的第一個記錄。

- ID_RECORD_LAST 將移至最後一筆記錄，在資料錄集。

- ID_RECORD_NEXT 將移至下一個資料錄集記錄。

- ID_RECORD_PREV 將移至前一筆記錄，在資料錄集。

### <a name="return-value"></a>傳回值

如果移動不成功則為非零否則為 0，表示移動要求遭到拒絕。

### <a name="remarks"></a>備註

預設實作會呼叫適當`Move`成員函式`CRecordset`資料錄檢視相關聯的物件。

根據預設，`OnMove`更新資料來源上目前的記錄，如果使用者資料錄檢視中已變更。

應用程式精靈 建立功能表資源的第一筆、 最後一筆記錄、 下一筆記錄和上一筆記錄的功能表項目。 如果您選取可停駐工具列選項，應用程式精靈 也建立工具列按鈕對應至這些命令。

如果您跳過資料錄集的最後一筆記錄時，[記錄] 檢視會繼續顯示最後一筆記錄。 如果您向後跳過第一筆記錄，[記錄] 檢視會繼續顯示第一筆記錄。

> [!CAUTION]
>  呼叫`OnMove`擲回例外狀況，如果資料錄集不有任何記錄。 呼叫適當的使用者介面更新處理常式函式 — `OnUpdateRecordFirst`， `OnUpdateRecordLast`， `OnUpdateRecordNext`，或`OnUpdateRecordPrev`— 相對應的移動作業，以判斷資料錄集是否有任何記錄。

## <a name="see-also"></a>另請參閱

[CFormView 類別](../../mfc/reference/cformview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)<br/>
[CFormView 類別](../../mfc/reference/cformview-class.md)
