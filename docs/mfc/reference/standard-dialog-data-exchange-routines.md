---
title: "標準對話方塊資料交換常式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ca598a9ac6a146457d24bcc80e54d003123d7dd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="standard-dialog-data-exchange-routines"></a>標準對話方塊資料交換常式
本主題列出用於通用的 MFC 對話方塊控制項的標準對話方塊資料交換 (DDX) 常式。  
  
> [!NOTE]
>  標準對話方塊資料交換常式定義於標頭檔 afxdd_.h。 不過，應用程式應該包括 afxwin.h。  
  
### <a name="ddx-functions"></a>DDX 函式  
  
|||  
|-|-|  
|[DDX_CBIndex](#ddx_cbindex)|初始化或擷取目前的選取範圍下拉式方塊控制項的索引。|  
|[DDX_CBString](#ddx_cbstring)|初始化或擷取目前的編輯欄位的下拉式方塊控制項的內容。|  
|[DDX_CBStringExact](#ddx_cbstringexact)|初始化或擷取目前的編輯欄位的下拉式方塊控制項的內容。|  
|[DDX_Check](#ddx_check)|初始化或擷取的核取方塊控制項的目前狀態。|  
|[DDX_Control](#ddx_control)|子類別的對話方塊內指定的控制項。|  
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|初始化或擷取日期和時間選擇器控制項的日期和/或時間資料。|  
|[DDX_IPAddress](#ddx_ipaddress)|初始化或擷取的 IP 位址控制項的目前值。|  
|[DDX_LBIndex](#ddx_lbindex)|初始化或擷取目前的選取範圍的清單方塊控制項的索引。|  
|[DDX_LBString](#ddx_lbstring)|初始化或擷取清單方塊控制項中的目前選取項目。|  
|[DDX_LBStringExact](#ddx_lbstringexact)|初始化或擷取清單方塊控制項中的目前選取項目。|
|[DDX_ManagedControl](#ddx_managedcontrol)|建立.NET 控制項比對控制項的資源 id。|  
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|初始化或擷取月曆控制項的目前值。|  
|[DDX_Radio](#ddx_radio)|初始化或擷取以 0 為基礎的索引選項控制群組內已選項控制項。|  
|[DDX_Scroll](#ddx_scroll)|初始化或擷取捲軸控制項的捲動方塊的目前位置。|  
|[DDX_Slider](#ddx_slider)|初始化或擷取滑桿控制項的捲動方塊的目前位置。|  
|[DDX_Text](#ddx_text)|初始化或擷取的編輯控制項的目前值。|  
  
##  <a name="ddx_cbindex"></a>DDX_CBIndex  
 `DDX_CBIndex`函式會管理的傳輸`int`在對話方塊中，下拉式方塊控制項之間的資料形成檢視或控制項檢視物件和`int`對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
```  
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 下拉式方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *索引*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_CBIndex`呼叫時，*索引*設為目前的下拉式方塊選取項目的索引。 如果未不選取任何項目，則*索引*設為 0。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_cbstring"></a>DDX_CBString  
 `DDX_CBString`函式會管理的傳輸`CString`的下拉式方塊控制項在對話方塊中，編輯控制項之間的資料形成檢視或控制項檢視物件和`CString`對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
```  
void AFXAPI DDX_CBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 下拉式方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *值*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_CBString`呼叫時，*值*設為目前的下拉式方塊選取項目。 如果未不選取任何項目，則*值*設為零長度的字串。  
  
> [!NOTE]
>  如果下拉式方塊的下拉式清單方塊，交換的值會限制為 255 個字元。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_cbstringexact"></a>DDX_CBStringExact  
 `DDX_CBStringExact`函式會管理的傳輸`CString`的下拉式方塊控制項在對話方塊中，編輯控制項之間的資料形成檢視或控制項檢視物件和`CString`對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
```  
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 下拉式方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *值*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_CBStringExact`呼叫時，*值*設為目前的下拉式方塊選取項目。 如果未不選取任何項目，則*值*設為零長度的字串。  
  
> [!NOTE]
>  如果下拉式方塊的下拉式清單方塊，交換的值會限制為 255 個字元。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_check"></a>DDX_Check  
 `DDX_Check`函式會管理的傳輸`int`在對話方塊中，核取方塊控制項之間的資料形成檢視或控制項檢視物件和`int`對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
```  
void AFXAPI DDX_Check(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 核取方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *值*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_Check`呼叫時，*值*設為核取方塊控制項的目前狀態。 如需可能的狀態值的清單，請參閱[BM_GETCHECK](http://msdn.microsoft.com/library/windows/desktop/bb775986) Windows SDK 中。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_control"></a>DDX_Control  
 `DDX_Control`函式的子類別所指定的控制項`nIDC`、 對話方塊、 表單檢視或控制項檢視物件。  
  
```  
void AFXAPI DDX_Control(
    CDataExchange* pDX,  
    int nIDC,  
    CWnd& rControl);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。  
  
 `nIDC`  
 要進行子類別化控制項的資源識別碼。  
  
 *rControl*  
 對話方塊、 表單檢視或控制項檢視物件與指定之控制項相關的成員變數參考。  
  
### <a name="remarks"></a>備註  
 `pDX` Framework 所提供物件時`DoDataExchange`呼叫函式。 因此，`DDX_Control`只應該覆寫中呼叫`DoDataExchange`。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_datetimectrl"></a>DDX_DateTimeCtrl  
 `DDX_DateTimeCtrl`函式會管理之間的日期和時間選擇器控制項的日期和/或時間資料傳輸 ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) 對話方塊方塊或表單檢視物件，也可能[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)對話方塊方塊或表單檢視物件的資料成員。  
  
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
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。 您不需要刪除此物件。  
  
 `nIDC`  
 成員變數與相關聯的日期和時間選擇器控制項的資源識別碼。  
  
 *值*  
 在前兩個版本中，參考`CTime`或`COleDateTime`成員變數、 對話方塊、 表單檢視或控制項檢視物件，用來交換資料。 在第三個版本中，參考`CString`資料成員的控制項檢視物件。  
  
### <a name="remarks"></a>備註  
 當`DDX_DateTimeCtrl`呼叫時，*值*設定為目前的日期和時間選擇器控制項或控制項的狀態會設為*值*，端視交換的方向。  
  
 在上面的第三個版本`DDX_DateTimeCtrl`管理傳送`CString`日期之間的資料時間控制項和[CString](../../atl-mfc-shared/reference/cstringt-class.md)的控制項檢視物件的資料成員。 使用目前的地區設定規則來格式化日期和時間格式化字串。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  

   

 
## <a name="ddx_managedcontrol"></a>DDX_ManagedControl
建立.NET 控制項比對控制項的資源 id。  
   
### <a name="syntax"></a>語法  
  ```  
template <typename T>  
void DDX_ManagedControl(  
     CDataExchange* pDX,   
     int nIDC,   
     CWinFormsControl<T>& control );  
```
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange 類別](cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 控制項的控制項屬性相關聯的資源識別碼。  
  
 `control`  
 若要參考[CWinFormsControl 類別](cwinformscontrol-class.md)物件。  
   
### <a name="remarks"></a>備註  
 `DDX_ManagedControl`呼叫[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)若要建立的比對資源的控制項 id。 使用`DDX_ManagedControl`建立控制項中的資源識別碼從[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)。 資料交換，您不需要使用 Windows Form 控制項的 DDX/DDV 函式。  
  
 如需詳細資訊，請參閱[How to： 使用 Windows Form 執行 DDX/DDV 資料繫](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)。  
   
### <a name="requirements"></a>需求  
 **標頭：** afxwinforms.h  
   
### <a name="see-also"></a>請參閱  
 [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)   
 [CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
 

  
##  <a name="ddx_ipaddress"></a>DDX_IPAddress  
 `DDX_IPAddress`函式會管理 IP 位址控制項和控制項檢視物件的資料成員之間的資料傳輸。  
  
```  
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,  
    int nIDC,  
    DWORD& value);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 IP 位址控制項的控制項屬性相關聯的資源識別碼。  
  
 *值*  
 若要參考`DWORD`包含四個欄位值的 IP 位址控制項。 欄位會填滿，或讀取，如下所示。  
  
|欄位|包含欄位值的位元|  
|-----------|-------------------------------------|  
|3|0 到 7|  
|2|8 到 15|  
|1|16 到 23|  
|0|24 到 31|  
  
 使用 Win32 [IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378)讀取值，或使用[IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380)来填入的值。 這些訊息是 Windows SDK 中所述。  
  
### <a name="remarks"></a>備註  
 當`DDX_IPAddress`呼叫時，*值*會從 IP 位址控制項，請讀取或*值*寫入至控制項，根據交換的方向。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_lbindex"></a>DDX_LBIndex  
 `DDX_LBIndex`函式會管理的傳輸`int`在對話方塊中，清單方塊控制項之間的資料形成檢視或控制項檢視物件和`int`對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
```  
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 清單方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *索引*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_LBIndex`呼叫時，*索引*設為目前的清單方塊選取項目的索引。 如果未不選取任何項目，則*索引*設定為-1。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_lbstring"></a>DDX_LBString  
 `DDX_LBString`函式會管理的傳輸`CString`在對話方塊中，清單方塊控制項之間的資料形成檢視或控制項檢視物件和`CString`對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
```  
void AFXAPI DDX_LBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 清單方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *值*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_LBString`呼叫以將資料傳送至清單方塊控制項，其開頭符合的控制項中的第一個項目*值*已選取。 (若要比對整個項目，而不是前置詞，使用[DDX_LBStringExact](#ddx_lbstringexact)。)如果沒有符合的成員，會不選取任何項目。 比對不區分大小寫。  
  
 當`DDX_LBString`呼叫以從清單方塊控制項，將資料傳送*值*設為目前的清單方塊選取項目。 如果未不選取任何項目，則*值*設為零長度的字串。  
  
> [!NOTE]
>  如果清單方塊的下拉式清單方塊，交換的值會限制為 255 個字元。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_lbstringexact"></a>DDX_LBStringExact  
 `DDX_CBStringExact`函式會管理的傳輸`CString`在對話方塊中，清單方塊控制項的編輯控制項之間的資料形成檢視或控制項檢視物件和`CString`對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
```  
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 清單方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *值*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_LBStringExact`呼叫以將資料傳送至清單方塊控制項，而符合之控制項中的第一個項目*值*已選取。 (若要符合的前置詞，而不是整個項目，使用[DDX_LBString](#ddx_lbstring)。)如果沒有符合的成員，會不選取任何項目。 比對不區分大小寫。  
  
 當`DDX_CBStringExact`呼叫以從清單方塊控制項，將資料傳送*值*設為目前的清單方塊選取項目。 如果未不選取任何項目，則*值*設為零長度的字串。  
  
> [!NOTE]
>  如果清單方塊的下拉式清單方塊，交換的值會限制為 255 個字元。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_monthcalctrl"></a>DDX_MonthCalCtrl  
 `DDX_MonthCalCtrl`函式會管理月曆控制項之間的日期資料傳輸 ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) 對話方塊、 表單檢視或控制項檢視物件，也可能[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
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
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。 您不需要刪除此物件。  
  
 `nIDC`  
 月曆控制項的資源識別碼相關聯的成員變數。  
  
 *值*  
 若要參考`CTime`或`COleDateTime`對話方塊、 表單檢視中，或用來交換資料的控制項檢視物件的成員變數。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  控制項管理日期值。 時間物件中的時間欄位會設定為反映控制項視窗的建立時間，或透過呼叫控制項中已設定的間隔時間`CMonthCalCtrl::SetCurSel`。  
  
 當`DDX_MonthCalCtrl`呼叫時，*值*設定月曆控制項的目前狀態。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_radio"></a>DDX_Radio  
 `DDX_Radio`函式會管理的傳輸`int`選項控制項在對話方塊中，群組之間的資料形成檢視或控制項檢視物件和`int`對話方塊、 表單檢視或控制項檢視物件的資料成員。 值`int`資料成員由決定根據哪一個選項按鈕群組中的已選取。  
  
```  
void AFXAPI DDX_Radio(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 第一個選項控制項群組中的資源識別碼。  
  
 *值*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_Radio`呼叫時，*值*設選項控制項群組的目前狀態。 的值設定為以 0 為基礎的索引選項控制項已，或會檢查為-1，如果沒有選擇控制項。  
  
 例如，在案例的第一個選項按鈕群組中的檢查 （WS_GROUP 樣式的按鈕） 的值`int`成員為 0，依此類推。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_scroll"></a>DDX_Scroll  
 `DDX_Scroll`函式會管理的傳輸`int`之間捲軸控制項在對話方塊中，資料表單檢視或控制項檢視物件和`int`對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
```  
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 捲軸控制項的控制項屬性相關聯的資源識別碼。  
  
 *值*  
 用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_Scroll`呼叫時，*值*設為控制項的捲動方塊目前的位置。 多個控制項的捲動方塊目前的位置與相關聯的值的詳細資訊，請參閱[GetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787585) Windows SDK 中。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_slider"></a>DDX_Slider  
 `DDX_Slider`函式會管理的傳輸`int`對話方塊或表單檢視中的滑桿控制項之間的資料和`int`對話方塊方塊或表單檢視物件的資料成員。  
  
```  
void AFXAPI DDX_Slider(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 滑桿控制項的資源識別碼。  
  
 *值*  
 交換值的參考。 這個參數會保存，或設定滑桿控制項的目前位置。  
  
### <a name="remarks"></a>備註  
 當`DDX_Slider`呼叫時，*值*設為目前的位置，控制項的捲動方塊，或值的接收位置，根據交換的方向。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 滑桿控制項的相關資訊，請參閱[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_text"></a>DDX_Text  
 `DDX_Text`函式會管理的傳輸`int`， **UINT**，**長**， `DWORD`， `CString`， **float**，或**double**在對話方塊中，編輯控制項之間的資料表單檢視，或控制項檢視和[CString](../../atl-mfc-shared/reference/cstringt-class.md)對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
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
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 編輯控制項在對話方塊、 表單檢視或控制項檢視物件的識別碼。  
  
 *值*  
 對話方塊、 表單檢視或控制項檢視物件中的資料成員參考。 資料型別*值*取決於哪一個多載版本`DDX_Text`您使用。  
  
### <a name="remarks"></a>備註  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  

### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  

## <a name="see-also"></a>請參閱  
 [標準對話方塊資料驗證常式](../../mfc/reference/standard-dialog-data-validation-routines.md)   
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)
