---
title: 標準對話方塊資料交換常式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 338412780116201b40e51ff38c4805097add4e3c
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885971"
---
# <a name="standard-dialog-data-exchange-routines"></a>標準對話方塊資料交換常式
本主題列出常見的 MFC 對話方塊控制項所使用的標準對話方塊資料交換 (DDX) 常式。  
  
> [!NOTE]
>  標準對話方塊資料交換常式會定義在標頭檔 afxdd_.h。 不過，應用程式應該包含 afxwin.h。  
  
### <a name="ddx-functions"></a>DDX 函式  
  
|||  
|-|-|  
|[DDX_CBIndex](#ddx_cbindex)|初始化或擷取目前的選取範圍下拉式方塊控制項的索引。|  
|[DDX_CBString](#ddx_cbstring)|初始化或擷取目前的編輯欄位的下拉式方塊控制項的內容。|  
|[DDX_CBStringExact](#ddx_cbstringexact)|初始化或擷取目前的編輯欄位的下拉式方塊控制項的內容。|  
|[DDX_Check](#ddx_check)|初始化或擷取的核取方塊控制項的目前狀態。|  
|[DDX_Control](#ddx_control)|子類別 對話方塊中指定的控制項。|  
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|初始化或擷取日期和/或時間之資料的日期和時間選擇器控制項。|  
|[DDX_IPAddress](#ddx_ipaddress)|初始化或擷取的 IP 位址控制項的目前值。|  
|[DDX_LBIndex](#ddx_lbindex)|初始化或擷取目前的選取範圍的清單方塊控制項的索引。|  
|[DDX_LBString](#ddx_lbstring)|初始化或擷取目前的選取範圍內的清單方塊控制項。|  
|[DDX_LBStringExact](#ddx_lbstringexact)|初始化或擷取目前的選取範圍內的清單方塊控制項。|
|[DDX_ManagedControl](#ddx_managedcontrol)|建立.NET 控制項，比對控制項的資源識別碼。|  
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|初始化或擷取月曆控制項的目前值。|  
|[DDX_Radio](#ddx_radio)|初始化或擷取 0 為基底的索引選項控制項目前簽選項控制群組內。|  
|[DDX_Scroll](#ddx_scroll)|初始化或擷取捲軸控制項的捲動方塊的目前位置。|  
|[DDX_Slider](#ddx_slider)|初始化或擷取滑桿控制項的捲動方塊的目前位置。|  
|[DDX_Text](#ddx_text)|初始化或擷取目前的編輯控制項的值。|  
  
##  <a name="ddx_cbindex"></a>  DDX_CBIndex  
 `DDX_CBIndex`函式可管理的傳輸**int**  對話方塊中，在下拉式方塊控制項之間的資料表單檢視或控制項檢視物件並**int**對話方塊、 表單檢視或控制項的資料成員檢視物件。  
  
```  
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>參數  
 *pDX*  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC*  
 下拉式方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *index*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數的參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_CBIndex`呼叫時， *index*設為目前的下拉式方塊選取項目的索引。 如果未不選取任何項目，則*index*設為 0。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_cbstring"></a>  DDX_CBString  
 `DDX_CBString`函式可管理的傳輸`CString`在對話方塊中，下拉式方塊控制項的編輯控制項之間的資料表單檢視或控制項檢視物件和`CString`對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
```  
void AFXAPI DDX_CBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>參數  
 *pDX*  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC*  
 下拉式方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *值*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數的參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_CBString`呼叫時，*值*設為目前的下拉式方塊選取項目。 如果未不選取任何項目，則*值*設為零長度的字串。  
  
> [!NOTE]
>  如果下拉式方塊的下拉式清單方塊，交換的值是限制為 255 個字元。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_cbstringexact"></a>  DDX_CBStringExact  
 `DDX_CBStringExact`函式可管理的傳輸`CString`在對話方塊中，下拉式方塊控制項的編輯控制項之間的資料表單檢視或控制項檢視物件和`CString`對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
```  
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>參數  
 *pDX*  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC*  
 下拉式方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *值*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數的參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_CBStringExact`呼叫時，*值*設為目前的下拉式方塊選取項目。 如果未不選取任何項目，則*值*設為零長度的字串。  
  
> [!NOTE]
>  如果下拉式方塊的下拉式清單方塊，交換的值是限制為 255 個字元。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_check"></a>  DDX_Check  
 `DDX_Check`函式可管理的傳輸**int**在對話方塊中，核取方塊控制項之間的資料表單檢視或控制項檢視物件並**int**對話方塊、 表單檢視或控制項的資料成員檢視物件。  
  
```  
void AFXAPI DDX_Check(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>參數  
 *pDX*  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC*  
 核取方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *值*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數的參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_Check`呼叫時，*值*設為核取方塊控制項的目前狀態。 如需可能的狀態值的清單，請參閱 < [BM_GETCHECK](http://msdn.microsoft.com/library/windows/desktop/bb775986) Windows SDK 中。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_control"></a>  DDX_Control  
 `DDX_Control`函數所指定的控制項的子類別*nIDC*、 對話方塊、 表單檢視或控制項檢視物件。  
  
```  
void AFXAPI DDX_Control(
    CDataExchange* pDX,  
    int nIDC,  
    CWnd& rControl);  
```  
  
### <a name="parameters"></a>參數  
 *pDX*  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。  
  
 *nIDC*  
 若要進行子類別化控制項的資源識別碼。  
  
 *rControl*  
 對話方塊、 表單檢視中或指定的控制項相關的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 *PDX* framework 所提供物件時`DoDataExchange`呼叫函式。 因此，`DDX_Control`只應該覆寫內呼叫`DoDataExchange`。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_datetimectrl"></a>  DDX_DateTimeCtrl  
 `DDX_DateTimeCtrl`函式可管理之間的日期和時間選擇器控制項的日期和/或時間的資料傳輸 ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) 對話方塊方塊或 表單檢視物件，並在[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)對話方塊方塊或 表單檢視物件的資料成員。  
  
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
 *pDX*  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。 您不需要刪除此物件。  
  
 *nIDC*  
 成員變數相關聯的日期和時間選擇器控制項的資源識別碼。  
  
 *值*  
 在前兩個版本中，參考`CTime`或`COleDateTime`成員變數、 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件。 在第三個版本中，參考`CString`資料成員控制項檢視物件。  
  
### <a name="remarks"></a>備註  
 當`DDX_DateTimeCtrl`呼叫時，*值*設定為目前的日期和時間選擇器控制項或控制項的狀態會設為*值*，取決於交換的方向。  
  
 在上述的第三個版本中`DDX_DateTimeCtrl`管理的傳輸`CString`日期之間的資料的時間控制項和[CString](../../atl-mfc-shared/reference/cstringt-class.md)的控制項檢視物件的資料成員。 使用目前的地區設定的規則來格式化日期和時間格式化字串。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  

## <a name="ddx_managedcontrol"></a>  DDX_ManagedControl
建立.NET 控制項，比對控制項的資源識別碼。  
   
### <a name="syntax"></a>語法  
```  
template <typename T>  
void DDX_ManagedControl(  
     CDataExchange* pDX,   
     int nIDC,   
     CWinFormsControl<T>& control );  
```
### <a name="parameters"></a>參數  
 *pDX*  
 指標[CDataExchange 類別](cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC*  
 控制項的控制項屬性相關聯的資源識別碼。  
  
 *control*  
 參考[CWinFormsControl 類別](cwinformscontrol-class.md)物件。  
   
### <a name="remarks"></a>備註  
 `DDX_ManagedControl` 呼叫[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)建立控制項，比對資源的控制項 id。 使用`DDX_ManagedControl`若要從資源識別碼，在建立控制項[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)。 資料交換，您不需要使用 Windows Form 控制項使用 DDX/DDV 函式。  
  
 如需詳細資訊，請參閱 <<c0> [ 如何： 使用 Windows Form 執行 DDX/DDV 資料繫](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)。  
   
### <a name="requirements"></a>需求  
 **標頭：** afxwinforms.h  
   
### <a name="see-also"></a>另請參閱  
 [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)   
 [CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
 

  
##  <a name="ddx_ipaddress"></a>  DDX_IPAddress  
 `DDX_IPAddress`函式可管理的 IP 位址控制項和控制項檢視物件的資料成員之間的資料傳輸。  
  
```  
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,  
    int nIDC,  
    DWORD& value);  
```  
  
### <a name="parameters"></a>參數  
 *pDX*  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC*  
 IP 位址相關聯的控制項與控制項屬性的資源識別碼。  
  
 *值*  
 包含四個欄位值的 IP 位址控制項的 DWORD 參考。 欄位會填入，或讀取，如下所示。  
  
|欄位|包含欄位值的位元|  
|-----------|-------------------------------------|  
|3|0 到 7|  
|2|8 到 15|  
|1|16 到 23|  
|0|24 到 31|  
  
 使用 Win32 [IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378)讀取值，或使用[IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380)來填滿值。 這些訊息會說明 Windows SDK。  
  
### <a name="remarks"></a>備註  
 當`DDX_IPAddress`呼叫時，*值*其中一個讀取從 IP 位址的控制項，或*值*寫入至控制項，根據交換的方向。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_lbindex"></a>  DDX_LBIndex  
 `DDX_LBIndex`函式可管理的傳輸**int**  對話方塊中，在清單方塊控制項之間的資料表單檢視或控制項檢視物件並**int**對話方塊、 表單檢視或控制項的資料成員檢視物件。  
  
```  
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>參數  
 *pDX*  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC*  
 清單方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *index*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數的參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_LBIndex`呼叫時， *index*設為目前的清單方塊選取項目索引。 如果未不選取任何項目，則*index*設定為-1。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_lbstring"></a>  DDX_LBString  
 `DDX_LBString`函式可管理的傳輸`CString` 對話方塊中，在清單方塊控制項之間的資料表單檢視或控制項檢視物件和`CString`對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
```  
void AFXAPI DDX_LBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>參數  
 *pDX*  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC*  
 清單方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *值*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數的參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_LBString`將資料傳送到清單方塊控制項，其開頭符合的控制項中的第一個項目會呼叫*值*已選取。 (若要比對整個項目，而不是前置詞，請使用[DDX_LBStringExact](#ddx_lbstringexact)。)如果不有任何相符項目，則會不選取任何項目。 比對不區分大小寫。  
  
 當`DDX_LBString`呼叫以將資料從清單方塊控制項，傳輸*值*設為目前的清單方塊選取項目。 如果未不選取任何項目，則*值*設為零長度的字串。  
  
> [!NOTE]
>  如果清單方塊的下拉式清單方塊，交換的值是限制為 255 個字元。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_lbstringexact"></a>  DDX_LBStringExact  
 `DDX_CBStringExact`函式可管理的傳輸`CString` 對話方塊中，在清單方塊控制項的編輯控制項之間的資料表單檢視或控制項檢視物件和`CString`對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
```  
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>參數  
 *pDX*  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC*  
 清單方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *值*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數的參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_LBStringExact`將資料傳送到清單方塊控制項，而符合控制項中的第一個項目會呼叫*值*已選取。 (若要符合的前置詞，而不是整個項目，使用[DDX_LBString](#ddx_lbstring)。)如果不有任何相符項目，則會不選取任何項目。 比對不區分大小寫。  
  
 當`DDX_CBStringExact`呼叫以將資料從清單方塊控制項，傳輸*值*設為目前的清單方塊選取項目。 如果未不選取任何項目，則*值*設為零長度的字串。  
  
> [!NOTE]
>  如果清單方塊的下拉式清單方塊，交換的值是限制為 255 個字元。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_monthcalctrl"></a>  DDX_MonthCalCtrl  
 `DDX_MonthCalCtrl`函式可管理日期間傳輸資料月曆控制項 ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) 中的對話方塊、 表單檢視或控制項檢視物件且[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
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
 *pDX*  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。 您不需要刪除此物件。  
  
 *nIDC*  
 月曆控制項的資源識別碼相關聯的成員變數。  
  
 *值*  
 參考`CTime`或`COleDateTime`對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  控制項會管理日期值。 階段物件中的時間欄位會設為反映 [控制] 視窗中，建立時間，或藉由呼叫控制項中已設定的間隔時間`CMonthCalCtrl::SetCurSel`。  
  
 當`DDX_MonthCalCtrl`呼叫時，*值*設為月曆控制項的目前狀態。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_radio"></a>  DDX_Radio  
 `DDX_Radio`函式可管理的傳輸**int**在對話方塊中，選項控制群組之間的資料表單檢視或控制項檢視物件並**int**對話方塊、 表單檢視或控制項的資料成員檢視物件。 值**int**資料成員決定根據哪一個選項按鈕群組中的已選取。  
  
```  
void AFXAPI DDX_Radio(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>參數  
 *pDX*  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC*  
 第一個選項控制項群組中的資源識別碼。  
  
 *值*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數的參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_Radio`呼叫時，*值*設選項控制項群組的目前狀態。 的值設定為 0 為基底控制項的索引選項，目前的選取，或如果沒有選項控制項為-1 會檢查。  
  
 比方說，在案例中的第一個選項按鈕群組中的檢查 （WS_GROUP 樣式的按鈕） 的值**int**成員為 0，依此類推。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_scroll"></a>  DDX_Scroll  
 `DDX_Scroll`函式可管理的傳輸**int**在對話方塊中，捲軸控制項之間的資料表單檢視或控制項檢視物件並**int**對話方塊、 表單檢視或控制項的資料成員檢視物件。  
  
```  
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>參數  
 *pDX*  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC*  
 捲軸控制項的控制項屬性相關聯的資源識別碼。  
  
 *值*  
 用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_Scroll`呼叫時，*值*設為控制項的捲動方塊的目前位置。 如需有關控制項的捲動方塊的目前位置相關聯的值的詳細資訊，請參閱[GetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787585) Windows SDK 中。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_slider"></a>  DDX_Slider  
 `DDX_Slider`函式可管理的傳輸**int** ] 對話方塊或表單檢視中的滑桿控制項之間的資料並**int**對話方塊方塊或 [表單檢視物件的資料成員。  
  
```  
void AFXAPI DDX_Slider(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>參數  
 *pDX*  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC*  
 滑桿控制項的資源識別碼。  
  
 *值*  
 要交換值的參考。 此參數保留或設定滑桿控制項的目前位置。  
  
### <a name="remarks"></a>備註  
 當`DDX_Slider`呼叫時，*值*設為目前位置之控制項的基本原則是，或值的接收位置，根據交換的方向。  
  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 滑桿控制項的相關資訊，請參閱[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddx_text"></a>  DDX_Text  
 `DDX_Text`函式可管理的傳輸**int**， **UINT**， **long**，DWORD， `CString`， **float**，或**雙**在對話方塊中，編輯控制項之間的資料表單檢視，或控制項檢視和[CString](../../atl-mfc-shared/reference/cstringt-class.md)對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
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
 *pDX*  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC*  
 在對話方塊、 表單檢視或控制項檢視物件中編輯控制項的 ID。  
  
 *值*  
 在對話方塊、 表單檢視或控制項檢視物件中的資料成員參考。 資料類型*值*取決於其中一個多載版本`DDX_Text`您使用。  
  
### <a name="remarks"></a>備註  
 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  

### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  

## <a name="see-also"></a>另請參閱  
 [標準對話方塊資料驗證常式](../../mfc/reference/standard-dialog-data-validation-routines.md)   
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
