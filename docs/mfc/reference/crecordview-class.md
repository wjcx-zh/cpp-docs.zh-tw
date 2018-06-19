---
title: CRecordView 類別 |Microsoft 文件
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
ms.openlocfilehash: 3784bfd637c40f326a67807d0002fae66177ac37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373481"
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
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|傳回非零，如果目前的記錄中相關聯的資料錄集的第一個記錄。|  
|[CRecordView::IsOnLastRecord](#isonlastrecord)|傳回非零，如果目前的記錄中相關聯的資料錄集的最後一個記錄。|  
|[CRecordView::OnGetRecordset](#ongetrecordset)|傳回衍生自此類別的物件的指標`CRecordset`。 ClassWizard 讓您覆寫這個函式，並在必要時建立資料錄集。|  
|[CRecordView::OnMove](#onmove)||  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRecordView::OnMove](#onmove)|如果目前的記錄已變更，更新資料來源，然後移至指定的記錄 （下一步、 前一個、 第一個或最後一個）。|  
  
## <a name="remarks"></a>備註  
 檢視是表單檢視，直接連接至`CRecordset`物件。 檢視從對話方塊範本資源建立並顯示欄位的`CRecordset`對話方塊範本的控制項中的物件。 `CRecordView`物件使用對話方塊資料交換 (DDX) 和資料錄欄位交換 (RFX) 以自動化的表單上的控制項之間的資料錄集欄位的資料移動。 `CRecordView` 也提供的預設實作移動到第一個下, 一個、 上一個或最後一筆和更新記錄目前的檢視介面。  
  
> [!NOTE]
>  如果您正在使用的資料存取物件 (DAO) 類別，而不是開放式資料庫連接 (ODBC) 類別，使用類別[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)改為。 如需詳細資訊，請參閱文章[概觀： 資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。  
  
 若要建立資料錄檢視最常見方式是使用應用程式精靈。 Tge 應用程式精靈建立資料錄檢視類別和其相關聯的資料錄集類別，做為基本架構起始應用程式的一部分。 如果您不要使用應用程式精靈建立資料錄檢視類別，可以使用 ClassWizard 稍後建立它。 如果您只需要在單一表單時，應用程式精靈方法是更容易。 類別可讓您決定使用資料錄檢視稍後在開發程序。 個別建立資料錄檢視和資料錄集，然後將它們連接至使用 ClassWizard 是最有彈性的方式，因為它讓您更能控制命名的資料錄集類別和其。H /。CPP 檔案。 這個方法也可讓您有多個資料錄檢視位於同一個資料錄集類別。  
  
 為了方便使用者記錄從移動資料錄檢視中，應用程式精靈建立功能表 （及選擇性地工具列） 移動資源至第一個下, 一個、 上一個或最後一個記錄。 如果您建立資料錄檢視類別與 ClassWizard 時，您需要建立這些資源自行使用功能表和點陣圖編輯器。  
  
 移動記錄記錄的預設實作的相關資訊，請參閱`IsOnFirstRecord`和`IsOnLastRecord`和文章[使用資料錄檢視](../../data/using-a-record-view-mfc-data-access.md)。  
  
 `CRecordView` 會追蹤的資料錄集中的使用者的位置，使資料錄檢視可以更新使用者介面。 當使用者移至資料錄集結尾時，資料錄檢視停用使用者介面物件，例如功能表項目或工具列按鈕 — 移動中相同的方向。  
  
 多個宣告和使用您的資料錄檢視和資料錄集類別的詳細資訊，請參閱 < 設計和建立資料錄檢視 >，文件中[資料錄檢視](../../data/record-views-mfc-data-access.md)。 如需記錄如何檢視工作和使用方式的詳細資訊，請參閱文章[使用資料錄檢視](../../data/using-a-record-view-mfc-data-access.md)。  
  
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
 當您建立的物件類型的衍生自`CRecordView`，呼叫可能是表單的建構函式來初始化檢視的物件，並識別基礎檢視的對話方塊資源。  
  
```  
explicit CRecordView(LPCTSTR lpszTemplateName);  
explicit CRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>參數  
 `lpszTemplateName`  
 包含的對話方塊範本資源名稱的以 null 結尾字串。  
  
 `nIDTemplate`  
 包含對話方塊範本資源的識別碼。  
  
### <a name="remarks"></a>備註  
 依名稱 （傳遞字串做為引數的建構函式） 或它的 ID （傳遞的不帶正負號的整數，做為引數），您可能可以識別資源。 建議使用的資源識別碼。  
  
> [!NOTE]
>  您的衍生的類別*必須*提供它自己的建構函式。 在衍生類別的建構函式，呼叫建構函式`CRecordView::CRecordView`資源名稱或識別碼當做引數，如下列範例所示。  
  
 **CRecordView::OnInitialUpdate**呼叫`UpdateData`，而它會呼叫`DoDataExchange`。 此一次呼叫`DoDataExchange`連接`CRecordView`（間接） 可控制`CRecordset`欄位 ClassWizard 所建立的資料成員。 這些資料成員不能直到之後呼叫的基底類別**CFormView::OnInitialUpdate**成員函式。  
  
> [!NOTE]
>  如果您使用 ClassWizard，精靈定義`enum`值`CRecordView::IDD`、 在類別宣告中，指定它，並建構函式使用成員初始設定清單中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]  
  
##  <a name="isonfirstrecord"></a>  CRecordView::IsOnFirstRecord  
 呼叫此成員函式，以判斷目前的記錄是否為此資料錄檢視相關聯的資料錄集物件中的第一個記錄。  
  
```  
BOOL IsOnFirstRecord();
```  
  
### <a name="return-value"></a>傳回值  
 如果目前的記錄資料錄集; 的第一個記錄為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 此函數非常適用於撰寫您自己的預設實作 ClassWizard 所撰寫的命令更新處理常式。  
  
 如果使用者移到第一筆記錄，架構會停用您具有移至第一個或前一筆記錄的任何使用者介面物件。  
  
##  <a name="isonlastrecord"></a>  CRecordView::IsOnLastRecord  
 呼叫此成員函式，以判斷目前的記錄是否為此資料錄檢視相關聯的資料錄集物件最後一筆記錄。  
  
```  
BOOL IsOnLastRecord();
```  
  
### <a name="return-value"></a>傳回值  
 如果目前的記錄筆資料錄集; 在非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 此函數非常適用於撰寫您自己的預設實作 ClassWizard 寫入移動記錄記錄的支援使用者介面的命令更新處理常式。  
  
> [!CAUTION]
>  此函式的結果是可靠的不同之處在於檢視無法偵測資料錄集的結尾，直到使用者已移動過。 資料錄檢視可以得知必須先停用移到下一個或最後一個記錄的任何使用者介面物件之前，使用者必須移動超過上一筆記錄。 如果使用者移動到超過最後一筆記錄以後，再移回至最後一筆記錄 （或之前），資料錄檢視可以追蹤使用者的資料錄集中的位置，並正確地停用使用者介面物件。 `IsOnLastRecord` 實作函式的呼叫之後也不可靠**OnRecordLast**，以處理`ID_RECORD_LAST`命令，或`CRecordset::MoveLast`。  
  
##  <a name="ongetrecordset"></a>  CRecordView::OnGetRecordset  
 將指標傳回至`CRecordset`-衍生的資料錄檢視相關聯的物件。  
  
```  
virtual CRecordset* OnGetRecordset() = 0;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`CRecordset`-衍生物件，如果物件已成功建立; 否則為**NULL**指標。  
  
### <a name="remarks"></a>備註  
 您必須覆寫此成員函式，來建構或取得資料錄集物件，並傳回的指標。 如果您宣告 ClassWizard 資料錄檢視類別，精靈會為您撰寫的預設覆寫。 ClassWizard 的預設實作會傳回資料錄集指標儲存在資料錄檢視中，如果有的話。 建構類型的資料錄集物件不是，如果您指定了與 ClassWizard 並呼叫其**開啟**成員開啟資料表，或執行查詢，函式，並再傳回物件的指標。  
  
 如需詳細資訊與範例，請參閱文章[資料錄檢視： 使用資料錄檢視](../../data/using-a-record-view-mfc-data-access.md)。  
  
##  <a name="onmove"></a>  CRecordView::OnMove  
 呼叫此成員函式，將移至不同的記錄資料錄集中，資料錄檢視控制項中顯示其欄位。  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>參數  
 `nIDMoveCommand`  
 其中一個的下列標準命令 ID 值：  
  
- `ID_RECORD_FIRST` 移至資料錄集中的第一個記錄。  
  
- `ID_RECORD_LAST` 資料錄集中移動至最後一筆記錄。  
  
- `ID_RECORD_NEXT` 移至資料錄集的下一個記錄。  
  
- `ID_RECORD_PREV` 移至資料錄集中的前一筆記錄。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果移動成功。否則為 0，如果移動要求被拒。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫適當**移動**成員函式`CRecordset`資料錄檢視相關聯的物件。  
  
 根據預設，`OnMove`更新目前的記錄資料來源上，如果使用者資料錄檢視中已變更。  
  
 應用程式精靈第一筆、 最後一筆記錄下, 一個記錄，以及上一筆記錄的功能表項目以建立功能表資源。 如果您選取可停駐工具列選項，應用程式精靈還會建立工具列含有對應至這些命令的按鈕。  
  
 如果您移動超過資料錄集中的最後一筆記錄，資料錄檢視會繼續顯示最後一筆記錄。 如果您向後移動超過第一筆資料錄，資料錄檢視會繼續顯示第一筆記錄。  
  
> [!CAUTION]
>  呼叫`OnMove`擲回例外狀況，如果資料錄集不有任何記錄。 呼叫適當的使用者介面更新處理常式函式 — **OnUpdateRecordFirst**， **OnUpdateRecordLast**， **OnUpdateRecordNext**，或**OnUpdateRecordPrev** — 之前對應移動運算，判斷資料錄集是否有任何記錄。  
  
## <a name="see-also"></a>另請參閱  
 [CFormView 類別](../../mfc/reference/cformview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)   
 [CFormView 類別](../../mfc/reference/cformview-class.md)
