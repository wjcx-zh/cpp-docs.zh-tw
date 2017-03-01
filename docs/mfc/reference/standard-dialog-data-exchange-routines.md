---
title: "標準對話方塊資料交換常式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 15bd88000a7a035ed416b7e1c0640488039079ab
ms.lasthandoff: 02/24/2017

---
# <a name="standard-dialog-data-exchange-routines"></a>標準對話方塊資料交換常式
本主題列出使用一般的 MFC 對話方塊控制項的標準對話方塊資料交換 (DDX) 常式。  
  
> [!NOTE]
>  標準對話方塊資料交換常式會定義在標頭檔 afxdd_.h。 不過，應用程式應包含 afxwin.h。  
  
### <a name="ddx-functions"></a>DDX 函式  
  
|||  
|-|-|  
|[DDX_CBIndex](#ddx_cbindex)|初始化或擷取目前的選取範圍下拉式方塊控制項的索引。|  
|[DDX_CBString](#ddx_cbstring)|初始化，或擷取目前的編輯欄位的下拉式方塊控制項的內容。|  
|[DDX_CBStringExact](#ddx_cbstringexact)|初始化，或擷取目前的編輯欄位的下拉式方塊控制項的內容。|  
|[DDX_Check](#ddx_check)|初始化或擷取的核取方塊控制項的目前狀態。|  
|[DDX_Control](#ddx_control)|子類別 對話方塊中指定的控制項。|  
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|初始化或擷取日期和/或時間的日期和時間選擇器控制項的資料。|  
|[DDX_IPAddress](#ddx_ipaddress)|初始化或擷取目前的 IP 位址控制項的值。|  
|[DDX_LBIndex](#ddx_lbindex)|初始化或擷取目前的選取範圍的清單方塊控制項的索引。|  
|[DDX_LBString](#ddx_lbstring)|初始化，或擷取清單方塊控制項中的目前選取範圍。|  
|[DDX_LBStringExact](#ddx_lbstringexact)|初始化，或擷取清單方塊控制項中的目前選取範圍。|  
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|初始化，或擷取月曆控制項的目前值。|  
|[DDX_Radio](#ddx_radio)|初始化或擷取已選項控制群組中選項按鈕控制項以 0 為基礎的索引。|  
|[DDX_Scroll](#ddx_scroll)|初始化，或擷取目前的捲動控制項的捲動方塊的位置。|  
|[DDX_Slider](#ddx_slider)|初始化，或擷取目前的滑桿控制項的捲動方塊的位置。|  
|[DDX_Text](#ddx_text)|初始化或擷取目前的編輯控制項的值。|  
  
##  <a name="a-nameddxcbindexa--ddxcbindex"></a><a name="ddx_cbindex"></a>DDX_CBIndex  
 `DDX_CBIndex`函式會管理傳送`int`在對話方塊中，下拉式方塊控制項之間的資料表單檢視或控制檢視物件和`int`對話方塊、 表單檢視或控制檢視物件的資料成員。  
  
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
 對話方塊、 表單檢視或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_CBIndex`呼叫時，*索引*設為目前的下拉式方塊選取項目索引。 如果未不選取任何項目，則*索引*設為 0。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxcbstringa--ddxcbstring"></a><a name="ddx_cbstring"></a>DDX_CBString  
 `DDX_CBString`函式會管理傳送`CString`之間的下拉式方塊控制項在對話方塊中，編輯控制項的資料表單檢視或控制檢視物件和`CString`對話方塊、 表單檢視或控制檢視物件的資料成員。  
  
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
  
 *value*  
 對話方塊、 表單檢視或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_CBString`呼叫時，*值*設為目前的下拉式方塊選取項目。 如果未不選取任何項目，則*值*設為零長度的字串。  
  
> [!NOTE]
>  如果下拉式方塊的下拉式清單方塊，交換的值是限制為 255 個字元。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxcbstringexacta--ddxcbstringexact"></a><a name="ddx_cbstringexact"></a>DDX_CBStringExact  
 `DDX_CBStringExact`函式會管理傳送`CString`之間的下拉式方塊控制項在對話方塊中，編輯控制項的資料表單檢視或控制檢視物件和`CString`對話方塊、 表單檢視或控制檢視物件的資料成員。  
  
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
  
 *value*  
 對話方塊、 表單檢視或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_CBStringExact`呼叫時，*值*設為目前的下拉式方塊選取項目。 如果未不選取任何項目，則*值*設為零長度的字串。  
  
> [!NOTE]
>  如果下拉式方塊的下拉式清單方塊，交換的值是限制為 255 個字元。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxchecka--ddxcheck"></a><a name="ddx_check"></a>DDX_Check  
 `DDX_Check`函式會管理傳送`int`在對話方塊中，核取方塊控制項之間的資料表單檢視或控制檢視物件和`int`對話方塊、 表單檢視或控制檢視物件的資料成員。  
  
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
  
 *value*  
 對話方塊、 表單檢視或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_Check`呼叫時，*值*設定為核取方塊控制項的目前狀態。 如需可能的狀態值，請參閱[BM_GETCHECK](http://msdn.microsoft.com/library/windows/desktop/bb775986)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxcontrola--ddxcontrol"></a><a name="ddx_control"></a>DDX_Control  
 `DDX_Control`函式的子類別所指定的控制項`nIDC`、 對話方塊、 表單檢視或控制檢視物件。  
  
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
 要進行子類別化控制項的資源 ID。  
  
 *rControl*  
 對話方塊、 表單檢視或指定之控制項相關的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 `pDX`架構所提供物件時`DoDataExchange`函式呼叫。 因此，`DDX_Control`只應該覆寫中呼叫`DoDataExchange`。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxdatetimectrla--ddxdatetimectrl"></a><a name="ddx_datetimectrl"></a>DDX_DateTimeCtrl  
 `DDX_DateTimeCtrl`函式管理之間的日期和時間選擇器控制項的日期和/或時間資料傳輸 ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md))] 對話方塊中或表單檢視物件，並在[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)對話方塊方塊或 [表單檢視物件的資料成員。  
  
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
 成員變數相關聯的日期和時間選擇器控制項的資源識別碼。  
  
 *value*  
 在前兩個版本中，參考`CTime`或`COleDateTime`成員變數、 對話方塊、 表單檢視或用來交換資料的控制項檢視物件。 在第三個版本中，參考`CString`資料成員控制項檢視物件。  
  
### <a name="remarks"></a>備註  
 當`DDX_DateTimeCtrl`呼叫時，*值*設定為目前日期和時間選擇器控制項或控制項的狀態設定為*值*，取決於交換的方向。  
  
 在上述的第三個版本`DDX_DateTimeCtrl`管理傳送`CString`資料之間的日期時間控制項和[CString](../../atl-mfc-shared/reference/cstringt-class.md)控制項檢視物件的資料成員。 使用目前的地區設定規則來格式化日期和時間格式化字串。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxipaddressa--ddxipaddress"></a><a name="ddx_ipaddress"></a>DDX_IPAddress  
 `DDX_IPAddress`函式會管理 IP 位址控制項和控制項的檢視物件的資料成員之間傳送資料。  
  
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
 控制項屬性相關聯的 IP 位址控制項的資源識別碼。  
  
 *value*  
 參考`DWORD`包含四個欄位值的 IP 位址控制項。 欄位會填滿，或讀取，如下所示。  
  
|欄位|包含欄位值的位元|  
|-----------|-------------------------------------|  
|3|0 到 7|  
|2|8 到 15|  
|1|16 到 23|  
|0|24 到 31|  
  
 使用 Win32 [IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378)讀取值，或使用[IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380)來填滿值。 這些訊息所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 當`DDX_IPAddress`呼叫時，*值*讀取從 IP 位址控制項或*值*會寫入至控制項，根據交換的方向。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxlbindexa--ddxlbindex"></a><a name="ddx_lbindex"></a>DDX_LBIndex  
 `DDX_LBIndex`函式會管理傳送`int`在對話方塊中，清單方塊控制項之間的資料表單檢視或控制檢視物件和`int`對話方塊、 表單檢視或控制檢視物件的資料成員。  
  
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
 對話方塊、 表單檢視或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_LBIndex`呼叫時，*索引*設為目前的清單方塊選取項目索引。 如果未不選取任何項目，則*索引*設定為-1。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxlbstringa--ddxlbstring"></a><a name="ddx_lbstring"></a>DDX_LBString  
 `DDX_LBString`函式會管理傳送`CString`在對話方塊中，清單方塊控制項之間的資料表單檢視或控制檢視物件和`CString`對話方塊、 表單檢視或控制檢視物件的資料成員。  
  
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
  
 *value*  
 對話方塊、 表單檢視或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_LBString`呼叫以將資料傳送至清單方塊控制項，控制項的開頭符合第一個項目*值*已選取。 (若要比對整個項目，而不是前置詞，使用[DDX_LBStringExact](#ddx_lbstringexact)。)如果沒有符合的成員，會不選取任何項目。 比對不區分大小寫。  
  
 當`DDX_LBString`將資料從清單方塊控制項，會呼叫*值*設為目前的清單方塊選取項目。 如果未不選取任何項目，則*值*設為零長度的字串。  
  
> [!NOTE]
>  如果清單方塊的下拉式清單方塊，交換的值是限制為 255 個字元。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxlbstringexacta--ddxlbstringexact"></a><a name="ddx_lbstringexact"></a>DDX_LBStringExact  
 `DDX_CBStringExact`函式會管理傳送`CString`在對話方塊中，清單方塊控制項的編輯控制項之間的資料表單檢視或控制檢視物件和`CString`對話方塊、 表單檢視或控制檢視物件的資料成員。  
  
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
  
 *value*  
 對話方塊、 表單檢視或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_LBStringExact`呼叫以將資料傳送至清單方塊控制項，控制項與第一個項目*值*已選取。 (若要符合的前置詞，而不是整個項目，使用[DDX_LBString](#ddx_lbstring)。)如果沒有符合的成員，會不選取任何項目。 比對不區分大小寫。  
  
 當`DDX_CBStringExact`將資料從清單方塊控制項，會呼叫*值*設為目前的清單方塊選取項目。 如果未不選取任何項目，則*值*設為零長度的字串。  
  
> [!NOTE]
>  如果清單方塊的下拉式清單方塊，交換的值是限制為 255 個字元。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxmonthcalctrla--ddxmonthcalctrl"></a><a name="ddx_monthcalctrl"></a>DDX_MonthCalCtrl  
 `DDX_MonthCalCtrl`函式管理之間月曆控制項的日期資料傳輸 ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) 對話方塊中，表單檢視或控制檢視物件，並在[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)對話方塊、 表單檢視或控制檢視物件的資料成員。  
  
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
  
 *value*  
 參考`CTime`或`COleDateTime`對話方塊、 表單檢視，或用來交換資料的控制項檢視物件的成員變數。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  控制項管理日期值。 時間物件中的時間欄位會設為反映控制項視窗的建立時間，或藉由呼叫控制項中設定的間隔時間`CMonthCalCtrl::SetCurSel`。  
  
 當`DDX_MonthCalCtrl`呼叫時，*值*設定月曆控制項的目前狀態。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxradioa--ddxradio"></a><a name="ddx_radio"></a>DDX_Radio  
 `DDX_Radio`函式會管理傳送`int`選項控制項在對話方塊中，群組之間的資料表單檢視或控制檢視物件和`int`對話方塊、 表單檢視或控制檢視物件的資料成員。 值`int`資料成員的決定，根據哪一個選項選取群組內的按鈕。  
  
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
 第一個選項按鈕控制項群組中的資源識別碼。  
  
 *value*  
 對話方塊、 表單檢視或用來交換資料的控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_Radio`呼叫時，*值*設為選項控制群組的目前狀態。 此值設定為以 0 為目前簽選項按鈕控制項的索引或-1，如果沒有選擇控制項會檢查。  
  
 例如，在第一個選項按鈕群組中的情況下檢查 （WS_GROUP 樣式的按鈕） 的值`int`成員為 0，依此類推。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxscrolla--ddxscroll"></a><a name="ddx_scroll"></a>DDX_Scroll  
 `DDX_Scroll`函式會管理傳送`int`在對話方塊中，捲軸控制項之間的資料表單檢視或控制檢視物件和`int`對話方塊、 表單檢視或控制檢視物件的資料成員。  
  
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
  
 *value*  
 用來交換資料之對話方塊、表單檢視或控制項檢視物件的成員變數參考。  
  
### <a name="remarks"></a>備註  
 當`DDX_Scroll`呼叫時，*值*設為目前控制項的捲動方塊的位置。 如需有關與控制項的捲動方塊目前的位置相關聯之值的詳細資訊，請參閱[GetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787585)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxslidera--ddxslider"></a><a name="ddx_slider"></a>DDX_Slider  
 `DDX_Slider`函式會管理傳送`int`對話方塊或表單檢視中的滑桿控制項之間的資料和`int`對話方塊方塊或 表單檢視物件的資料成員。  
  
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
  
 *value*  
 交換值的參考。 這個參數保留或設定滑桿控制項的目前位置。  
  
### <a name="remarks"></a>備註  
 當`DDX_Slider`呼叫時，*值*會設定為控制項的基本原則是，目前位置或接收位置，根據交換方向的值。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 關於滑桿控制項的資訊，請參閱[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="a-nameddxtexta--ddxtext"></a><a name="ddx_text"></a>DDX_Text  
 `DDX_Text`函式會管理傳送`int`， **UINT**，**長**， `DWORD`， `CString`， **float**，或**雙**表單檢視，在對話方塊中，編輯控制項之間的資料，或控制檢視和[CString](../../atl-mfc-shared/reference/cstringt-class.md)對話方塊、 表單檢視或控制檢視物件的資料成員。  
  
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
 編輯控制項在對話方塊、 表單檢視或控制檢視物件的識別碼。  
  
 *value*  
 對話方塊、 表單檢視或控制檢視物件中的資料成員的參考。 資料型別*值*取決於哪一個多載版本`DDX_Text`您使用。  
  
### <a name="remarks"></a>備註  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  

### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  

## <a name="see-also"></a>另請參閱  
 [標準對話方塊資料驗證常式](../../mfc/reference/standard-dialog-data-validation-routines.md)   
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

