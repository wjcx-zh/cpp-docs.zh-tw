---
title: COleDBRecordView 類別
ms.date: 11/04/2016
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
ms.openlocfilehash: de9c602cb747ee3d4449df479530e55ce907cb8a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366109"
---
# <a name="coledbrecordview-class"></a>COleDBRecordView 類別

在控制項中顯示資料庫記錄的檢視。

## <a name="syntax"></a>語法

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[COleDB記錄檢視:COleDB記錄檢視](#coledbrecordview)|建構 `COleDBRecordView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDB 記錄檢視::OnGetRowset](#ongetrowset)|返回標準 HRESULT 值。|
|[COleDB 記錄檢視::移動](#onmove)|更新數據來源上的目前記錄(如果髒),然後移動到指定的記錄(下一個、上一個、第一個或最後一個)。|

## <a name="remarks"></a>備註

視圖是直接連接到`CRowset`物件的表單檢視。 視圖是從對話方塊樣本資源創建的,並在對話方塊範本的控制項中`CRowset`顯示 物件的欄位。 對`COleDBRecordView`象 使用對話框資料交換 (DDX)`CRowset`和 內置 的導航功能來自動在窗體上的控制項和行集的欄位之間行動資料。 `COleDBRecordView`還提供用於移動到第一個、下一個、上一個或最後一個記錄的預設實現,以及用於更新當前查看的記錄的介面。

您可以使用 DDX`COleDbRecordView`函數 直接從資料庫記錄集中獲取數據,並將其顯示在對話方塊控制項中。 應使用`DDX_*``DDX_Text`方法(如 ),而不是`DDX_Field*``DDX_FieldText``COleDbRecordView`使用的函數(如 )。 `DDX_FieldText`將不起作用`COleDbRecordView`,`DDX_FieldText`因為需要鍵`CRecordset*``CRecordView`入 ()`CDaoRecordset*``CDaoRecordView`或 (的 ) 的其他參數。

> [!NOTE]
> 如果使用數據存取物件 (DAO) 類別而不是 OLE DB 使用者樣本類,請使用類[CDaoRecordView。](../../mfc/reference/cdaorecordview-class.md) 有關詳細資訊,請參閱文章[概述:資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

`COleDBRecordView`追蹤使用者在行集中的位置,以便記錄檢視可以更新使用者介面。 當使用者移動到行集的任一端時,記錄檢視將禁用使用者介面物件(如功能表項或工具列按鈕)以向同一方向進一步移動。

有關行集類的詳細資訊,請參閱[使用 OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>需求

**標題:** afxoledb.h

## <a name="coledbrecordviewcoledbrecordview"></a><a name="coledbrecordview"></a>COleDB記錄檢視:COleDB記錄檢視

建構 `COleDBRecordView` 物件。

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>參數

*lpszTemplate 名稱*<br/>
包含一個 null 連接端字串,該字串是對話方塊樣本資源的名稱。

*nIDTemplate*<br/>
包含對話方塊樣本資源的 ID 號。

### <a name="remarks"></a>備註

創建派生自`COleDBRecordView`的類型的物件時,請調用其中一個構造函數來創建視圖物件並標識視圖所基於的對話框資源。 您可以按名稱(將字串作為參數傳遞給建構函數)或通過其 ID(傳遞未簽名的整數作為參數)標識資源。

> [!NOTE]
> 派生類*必須*提供其自己的構造函數。 在建構函數中,調用建構函數,`COleDBRecordView::COleDBRecordView`將資源名稱或 ID 作為參數。

## <a name="coledbrecordviewongetrowset"></a><a name="ongetrowset"></a>COleDB 記錄檢視::OnGetRowset

返回與記錄檢視關聯的**CRowset<>** 物件的句柄。

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

必須重寫此成員函數以構造或獲取行集物件,並將句柄返回給該物件。 如果使用 ClassWizard 聲明記錄檢視類,精靈將為您編寫預設覆蓋。 ClassWizard 的預設實現返回存儲在記錄視圖中的行集句柄(如果存在)。 如果沒有,它將建構使用 ClassWizard 指定的類型的排集物件,並調用`Open`其成員 函數打開表或運行查詢,然後向該物件返回句柄。

> [!NOTE]
> 在 MFC 7.0`OnGetRowset``CRowset`之前,返回指向的指標。 如果代碼呼叫`OnGetRowset`,則需要將傳回類型變更為暫時化類別**CRowset<>**。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

有關詳細資訊和範例,請參閱[文章記錄檢視:使用紀錄檢視](../../data/using-a-record-view-mfc-data-access.md)。

## <a name="coledbrecordviewonmove"></a><a name="onmove"></a>COleDB 記錄檢視::移動

移動到行集中中的不同記錄,並在記錄檢視的控制項中顯示其欄位。

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>參數

*nIDMove命令*<br/>
以下標準命令 ID 值之一:

- ID_RECORD_FIRST = 移動到記錄集中的第一個記錄。

- ID_RECORD_LAST = 移動到記錄集中的最後一個記錄。

- ID_RECORD_NEXT = 移動到記錄集中的下一個記錄。

- ID_RECORD_PREV = 移動到記錄集中的上一條記錄。

### <a name="return-value"></a>傳回值

如果移動成功,則非零;否則 0 如果移動請求被拒絕。

### <a name="remarks"></a>備註

預設實現調用與記錄檢視`Move`關聯的`CRowset`物件的相應成員函數。

預設情況下,`OnMove`如果使用者在記錄檢視中更改了資料來源上的現記錄,則更新該紀錄。

"應用程式精靈"創建具有"第一條記錄"、"最後一條記錄"、"下一個記錄"和"上一個記錄"功能表項的功能表資源。 如果選擇「可停靠工具列」選項,「應用程式精靈」還會創建一個工具列,其中按鈕對應於這些命令。

如果移動超過記錄集中的最後一條記錄,記錄視圖將繼續顯示最後一條記錄。 如果向後移動超過第一條記錄,則記錄視圖將繼續顯示第一條記錄。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)
