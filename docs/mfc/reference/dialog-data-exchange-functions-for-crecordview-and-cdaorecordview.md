---
title: "對話方塊資料交換函式 CRecordView 和 CDaoRecordView 的 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DDX_Field functions
- ODBC [C++], dialog data exchange (DDX) support
- DDX (dialog data exchange) [C++], database support
- DDX (dialog data exchange) [C++], functions
- databases [C++], dialog data exchange (DDX) support
- DAO [C++], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
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
ms.openlocfilehash: 682c845aa2c915be69aee0d5e95f820573cd6084
ms.lasthandoff: 02/24/2017

---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>CRecordView 和 CDaoRecordView 的對話方塊資料交換函式
本主題列出用來交換資料之間的 DDX_Field 函式[CRecordset](../../mfc/reference/crecordset-class.md)和[CRecordView](../../mfc/reference/crecordview-class.md)表單或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)表單。  
  
> [!NOTE]
>  DDX_Field 函式的 DDX 函式類似交換控制項在表單中的資料。 但不同於 DDX，交換與檢視相關聯的資料錄集物件的欄位，而不是欄位的資料錄檢視本身的資料。 如需詳細資訊，請參閱類別`CRecordView`和`CDaoRecordView`。  
  
### <a name="ddxfield-functions"></a>DDX_Field 函式  
  
|||  
|-|-|  
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|整數資料傳輸的資料錄集欄位資料成員和下拉式方塊中目前選取的索引之間[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)。|  
|[DDX_FieldCBString](#ddx_fieldcbstring)|傳輸`CString`資料之間的資料錄集欄位資料成員和編輯控制項的下拉式方塊中`CRecordView`或`CDaoRecordView`。 時將資料從資料錄集移至控制項，此函式會以指定字串中字元開頭，下拉式方塊中選取的項目。|  
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|傳輸`CString`資料之間的資料錄集欄位資料成員和編輯控制項的下拉式方塊中`CRecordView`或`CDaoRecordView`。 移動資料時從資料錄集的控制項，此函式會完全符合指定的字串的下拉式方塊中選取的項目。|  
|[DDX_FieldCheck](#ddx_fieldcheck)|資料錄集欄位資料成員與核取方塊之間轉送布林資料`CRecordView`或`CDaoRecordView`。|  
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|整數資料傳輸的資料錄集欄位資料成員和目前的選取範圍中的清單方塊中的索引之間`CRecordView`或`CDaoRecordView`。|  
|[DDX_FieldLBString](#ddx_fieldlbstring)|管理傳送[CString](../../atl-mfc-shared/reference/cstringt-class.md)清單方塊控制項和資料錄集的欄位資料成員之間的資料。 移動資料時從資料錄集的控制項，此函式是以指定字串中字元的清單方塊選取的項目。|  
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|管理傳送`CString`清單方塊控制項和資料錄集的欄位資料成員之間的資料。 將資料從資料錄集移至控制項，此函式會選取完全符合指定的字串的第一個項目。|  
|[DDX_FieldRadio](#ddx_fieldradio)|整數資料傳輸的資料錄集欄位資料成員中的選項按鈕群組之間`CRecordView`或`CDaoRecordView`。|  
|[DDX_FieldScroll](#ddx_fieldscroll)|設定或取得在捲軸的捲動位置`CRecordView`或`CDaoRecordView`。 從呼叫程式[DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)函式。|  
|[DDX_FieldText](#ddx_fieldtext)|多載的版本可供傳輸`int`， **UINT**，**長**， `DWORD`， [CString](../../atl-mfc-shared/reference/cstringt-class.md)， **float**，**雙**，**簡短**， [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)，和[COleCurrency](../../mfc/reference/colecurrency-class.md)資料之間的資料錄集欄位資料成員和編輯方塊中`CRecordView`或`CDaoRecordView`。|  
  
##  <a name="a-nameddxfieldcbindexa--ddxfieldcbindex"></a><a name="ddx_fieldcbindex"></a>DDX_FieldCBIndex  
 `DDX_FieldCBIndex`函式會同步處理選取的項目在清單方塊控制項的資料錄檢視中的下拉式方塊控制項中的索引和`int`資料錄檢視相關聯的資料錄集欄位資料成員。  
  
```  
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,    
    int nIDC,   
    int& index,  
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,    
    int nIDC,   
    int& index,  
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 中的控制項 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *索引*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 此函式時將資料從資料錄集移至控制項，設定在控制項中指定的值為基礎的選項*索引*。 在從資料錄集傳輸至控制項，如果資料錄集欄位為 Null，MFC 會設定索引的值為 0。 在從控制項傳輸至資料錄集，如果控制項為空白，或選取任何項目時，資料錄集欄位是設定為 0。  
  
 如果您正在使用 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用的 DAO 架構類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 此範例也類似`DDX_FieldCBIndex`。  

### <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  

##  <a name="a-nameddxfieldcbstringa--ddxfieldcbstring"></a><a name="ddx_fieldcbstring"></a>DDX_FieldCBString  
 `DDX_FieldCBString`函式會管理傳送[CString](../../atl-mfc-shared/reference/cstringt-class.md)之間的資料錄檢視中的下拉式方塊控制項的編輯控制項的資料和`CString`資料錄檢視相關聯的資料錄集欄位資料成員。  
  
```  
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 中的控制項 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *value*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 此函式時將資料從資料錄集移至控制項，設定下拉式方塊中指定的字串中的字元為開頭的第一個資料列中目前選取範圍*值*。 從資料錄集傳輸至控制項，在資料錄集欄位為 Null，如果任何選取範圍從下拉式方塊中移除，然後編輯控制項的下拉式方塊設為空白。 在從控制項傳輸至資料錄集，如果控制項是空的資料錄集欄位是設定為 Null 如果允許欄位。  
  
 如果您正在使用 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用的 DAO 架構類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 此範例包含呼叫`DDX_FieldCBString`。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
## <a name="a-nameddxfieldcbstringexacta--ddxfieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a>DDX_FieldCBStringExact  
 `DDX_FieldCBStringExact`函式會管理傳送[CString](../../atl-mfc-shared/reference/cstringt-class.md)之間的資料錄檢視中的下拉式方塊控制項的編輯控制項的資料和`CString`資料錄檢視相關聯的資料錄集欄位資料成員。  
  
```  
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 中的控制項 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *value*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 此函式時將資料從資料錄集移至控制項，會將目前的選取範圍，完全符合指定之字串的第一個資料列的下拉式方塊中*值*。 從資料錄集傳輸至控制項，在資料錄集欄位為 NULL，如果任何選取項目已從下拉式方塊和下拉式方塊的編輯方塊會設為空白。 在從控制傳輸至資料錄集，如果控制項是空的資料錄集欄位設為 NULL。  
  
 如果您正在使用 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用的 DAO 架構類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 呼叫`DDX_FieldCBStringExact`會很類似。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="a-nameddxfieldchecka--ddxfieldcheck"></a><a name="ddx_fieldcheck"></a>DDX_FieldCheck  
 `DDX_FieldCheck`函式會管理傳送`int`在對話方塊中，核取方塊控制項之間的資料表單檢視或控制檢視物件和`int`對話方塊、 表單檢視或控制檢視物件的資料成員。  
  
```  
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 核取方塊控制項的控制項屬性相關聯的資源識別碼。  
  
 *value*  
 對話方塊、 表單檢視或用來交換資料的控制項檢視物件的成員變數參考。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 當`DDX_FieldCheck`呼叫時，*值*設定為核取方塊控制項的目前狀態或控制項的狀態會設為*值*，端視傳送的方向。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="a-nameddxfieldlbindexa--ddxfieldlbindex"></a><a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex  
 `DDX_FieldLBIndex`函式會同步處理選取的項目記錄檢視的清單方塊控制項中的索引和`int`資料錄檢視相關聯的資料錄集欄位資料成員。  
  
```  
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,    
    int nIDC,   
    int& index,  
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,    
    int nIDC,   
    int& index,  
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 中的控制項 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *索引*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 此函式時將資料從資料錄集移至控制項，設定在控制項中指定的值為基礎的選項*索引*。 在從資料錄集傳輸至控制項，如果資料錄集欄位為 Null，MFC 會設定索引的值為 0。 在從控制項傳輸至資料錄集，如果控制項是空的資料錄集欄位是設定為 0。  
  
 如果您正在使用 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用的 DAO 架構類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="a-nameddxfieldlbstringa--ddxfieldlbstring"></a><a name="ddx_fieldlbstring"></a>DDX_FieldLBString  
 `DDX_FieldLBString`清單方塊控制項中的目前選取範圍複製到資料錄檢視[CString](../../atl-mfc-shared/reference/cstringt-class.md)資料錄檢視相關聯的資料錄集欄位資料成員。  
  
```  
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 中的控制項 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *value*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 相反的方向，此函式會將目前的選取項目在清單方塊中所指定之字串的字元為開頭的第一個資料列*值*。 從資料錄集傳輸至控制項，在資料錄集欄位是 Null，如果任何選取項目會移除從清單方塊。 在從控制傳輸至資料錄集，如果控制項是空的資料錄集欄位設為 Null。  
  
 如果您正在使用 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用的 DAO 架構類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 呼叫`DDX_FieldLBString`會很類似。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="a-nameddxfieldlbstringexacta--ddxfieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact  
 `DDX_FieldLBStringExact`函式將清單方塊控制項中的目前選取範圍複製至資料錄檢視[CString](../../atl-mfc-shared/reference/cstringt-class.md)資料錄檢視相關聯的資料錄集欄位資料成員。  
  
```  
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 中的控制項 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *value*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 相反的方向，此函式會將目前的選取範圍完全符合指定之字串的第一個資料列的清單方塊中*值*。 從資料錄集傳輸至控制項，在資料錄集欄位是 Null，如果任何選取項目會移除從清單方塊。 在從控制傳輸至資料錄集，如果控制項是空的資料錄集欄位設為 Null。  
  
 如果您正在使用 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用的 DAO 架構類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 呼叫`DDX_FieldLBStringExact`會很類似。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="a-nameddxfieldradioa--ddxfieldradio"></a><a name="ddx_fieldradio"></a>DDX_FieldRadio  
 `DDX_FieldRadio`函式將以零為起始`int`與目前選取的選項按鈕群組的選項按鈕，在 [記錄] 檢視中的資料錄檢視的資料錄集的成員變數。  
  
```  
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 識別碼的第一個群組中 (使用樣式**WS_GROUP**) 相鄰的選項按鈕控制項中的[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *value*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 當從資料錄集欄位傳送到 檢視，此函式會開啟*第 n 個*選項按鈕 （以零為起始），然後關閉 其他 按鈕。 相反的方向，此函式會將資料錄集欄位是目前的 （核取） 的選項按鈕的序號。 在從資料錄集傳輸至控制項，如果資料錄集欄位為 Null，就會選取沒有按鈕。 在從控制傳輸至資料錄集，如果未不選取任何控制項，則資料錄集欄位是如果設為 Null 欄位允許的。  
  
 如果您正在使用 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用的 DAO 架構類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 呼叫`DDX_FieldRadio`會很類似。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="a-nameddxfieldscrolla--ddxfieldscroll"></a><a name="ddx_fieldscroll"></a>DDX_FieldScroll  
 `DDX_FieldScroll`函式會同步處理資料錄檢視中的捲軸捲軸位置和`int`資料錄檢視與 （或您選擇將它對應至任何整數變數） 相關聯的資料錄集欄位資料成員。  
  
```  
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *nIDC\**  
 識別碼的第一個群組中 (使用樣式**WS_GROUP**) 相鄰的選項按鈕控制項中的[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *value*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 當您將資料從資料錄集移至控制項，此函式會設定捲軸控制項的捲動位置中指定的值*值*。 在從資料錄集傳輸至控制項，如果資料錄集欄位為 Null，捲軸控制項是設定為 0。 在從控制傳輸至資料錄集，如果控制項是空的資料錄集欄位的值為 0。  
  
 如果您正在使用 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用的 DAO 架構類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 呼叫`DDX_FieldScroll`會很類似。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="a-nameddxfieldtexta--ddxfieldtext"></a><a name="ddx_fieldtext"></a>DDX_FieldText  
 `DDX_FieldText`函式會管理傳送`int`，**簡短**，**長**， `DWORD`， [CString](../../atl-mfc-shared/reference/cstringt-class.md)， **float**，**雙**， **BOOL**，或**位元組**的編輯方塊控制項和資料錄集的欄位資料成員之間的資料。  
  
```  
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    BYTE& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    UINT& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    long& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    DWORD& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    float& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    double& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    short& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    BOOL& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    BYTE& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    long& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    DWORD& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    float& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    double& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    COleDateTime& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    COleCurrency& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 中的控制項 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *value*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。 值的資料型別取決於哪一個多載版本`DDX_FieldText`您使用。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。 這個指標可讓`DDX_FieldText`偵測及設定 Null 值。  
  
### <a name="remarks"></a>備註  
 如[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件，`DDX_FieldText`也會管理傳送[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)，和[COleCurrency](../../mfc/reference/colecurrency-class.md)值。 空白的編輯方塊控制項表示 Null 值。 在從資料錄集傳輸至控制項，如果資料錄集欄位為 Null 的編輯方塊會設為空白。 在從控制傳輸至資料錄集，如果控制項是空的資料錄集欄位設為 Null。  
  
 使用與版本[CRecordset](../../mfc/reference/crecordset-class.md)參數，如果您正在使用 ODBC 為基礎的類別。 使用與版本[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)參數，如果您正在使用的 DAO 架構類別。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 如需範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 下列`DoDataExchange`函式的[CRecordView](../../mfc/reference/crecordview-class.md)包含`DDX_FieldText`函式會呼叫下列三種資料類型︰`IDC_COURSELIST`是一個下拉式方塊中，兩個控制項的編輯方塊。 DAO 程式設計*m_pSet*參數是一個指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 [!code-cpp[NVC_MFCDatabase #&43;](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]  

  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
    
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

