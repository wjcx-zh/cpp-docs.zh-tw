---
title: 對話方塊資料交換函式 CRecordView 和 CDaoRecordView 的 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
dev_langs:
- C++
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f58b7ba7ae51c4db065cd7b30cc233128f7b7c68
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>CRecordView 和 CDaoRecordView 的對話方塊資料交換函式
本主題列出用來交換資料之間的 DDX_Field 函式[CRecordset](../../mfc/reference/crecordset-class.md)和[CRecordView](../../mfc/reference/crecordview-class.md)表單或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)表單。  
  
> [!NOTE]
>  DDX_Field 函式的 DDX 函式類似，在於它們交換控制項在表單中的資料。 但不同於 DDX，交換資料的檢視相關聯的資料錄集物件的欄位，而非本身的資料錄檢視的欄位。 如需詳細資訊，請參閱類別`CRecordView`和`CDaoRecordView`。  
  
### <a name="ddxfield-functions"></a>DDX_Field 函式  
  
|||  
|-|-|  
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|傳輸整數資料之間的資料錄集欄位資料成員和下拉式方塊中目前選取範圍索引[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)。|  
|[DDX_FieldCBString](#ddx_fieldcbstring)|傳輸`CString`資料之間的資料錄集欄位資料成員和編輯控制項的下拉式方塊中`CRecordView`或`CDaoRecordView`。 移動資料時從資料錄集的控制項，此函式會以指定字串中字元開頭的下拉式方塊中選取的項目。|  
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|傳輸`CString`資料之間的資料錄集欄位資料成員和編輯控制項的下拉式方塊中`CRecordView`或`CDaoRecordView`。 移動資料時從資料錄集的控制項，此函式會完全符合指定的字串的下拉式方塊中選取的項目。|  
|[DDX_FieldCheck](#ddx_fieldcheck)|傳輸布林值資料之間的資料錄集欄位資料成員內的核取方塊`CRecordView`或`CDaoRecordView`。|  
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|傳輸整數資料之間的資料錄集欄位資料成員和清單方塊中目前選取範圍索引`CRecordView`或`CDaoRecordView`。|  
|[DDX_FieldLBString](#ddx_fieldlbstring)|管理傳送[CString](../../atl-mfc-shared/reference/cstringt-class.md)清單方塊控制項和資料錄集的欄位資料成員之間的資料。 移動資料時從資料錄集的控制項，此函式會以指定字串中字元開頭，清單方塊中選取的項目。|  
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|管理傳送`CString`清單方塊控制項和資料錄集的欄位資料成員之間的資料。 將資料從資料錄集移至控制項，此函式會選取完全符合指定的字串的第一個項目。|  
|[DDX_FieldRadio](#ddx_fieldradio)|傳輸的資料錄集欄位資料成員與中的選項按鈕群組之間的整數資料`CRecordView`或`CDaoRecordView`。|  
|[DDX_FieldScroll](#ddx_fieldscroll)|設定或取得捲軸控制項的捲動位置`CRecordView`或`CDaoRecordView`。 從呼叫程式[DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)函式。|  
|[DDX_FieldSlider](#ddx_fieldslider)|同步處理資料錄檢視中的滑桿控制項捲動方塊位置和`int`資料錄集的欄位資料成員。 |
|[DDX_FieldText](#ddx_fieldtext)|多載的版本可供傳送`int`， **UINT**，**長**， `DWORD`， [CString](../../atl-mfc-shared/reference/cstringt-class.md)， **float****double**，**簡短**， [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)，和[COleCurrency](../../mfc/reference/colecurrency-class.md)之間的資料錄集欄位資料成員和編輯的資料方塊`CRecordView`或`CDaoRecordView`。|  
  
##  <a name="ddx_fieldcbindex"></a>  DDX_FieldCBIndex  
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
 中的控制項識別碼[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *index*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 移動資料時從資料錄集的控制項，此函數會設定控制項中指定的值為基礎的選取項目*索引*。 在從資料錄集傳輸至控制項，如果資料錄集欄位為 Null，MFC 會設定索引的值為 0。 在從控制項傳輸至資料錄集，如果控制項為空白，或選取任何項目時，資料錄集欄位是設定為 0。  
  
 如果您正在使用的 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用 DAO 類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 此範例也類似`DDX_FieldCBIndex`。  

### <a name="requirements"></a>需求  
 **標頭：** afxdao.h  

##  <a name="ddx_fieldcbstring"></a>  DDX_FieldCBString  
 `DDX_FieldCBString`函式會管理的傳輸[CString](../../atl-mfc-shared/reference/cstringt-class.md)之間的資料錄檢視中的下拉式方塊控制項的編輯控制項的資料和`CString`資料錄檢視相關聯的資料錄集欄位資料成員。  
  
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
 中的控制項識別碼[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *值*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 移動資料時從資料錄集的控制項，此函數會設定目前選取範圍開頭中指定的字串中字元的第一個資料列的下拉式方塊中*值*。 上從資料錄集傳輸至控制項，如果資料錄集欄位為 Null，任一選取項目已從下拉式方塊和下拉式方塊編輯控制項設定為空白。 在從控制項傳輸至資料錄集，如果控制項是空的資料錄集欄位設為 Null 若欄位允許。  
  
 如果您正在使用的 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用 DAO 類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 此範例包含呼叫`DDX_FieldCBString`。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
## <a name="ddx_fieldcbstringexact"></a>  DDX_FieldCBStringExact  
 `DDX_FieldCBStringExact`函式會管理的傳輸[CString](../../atl-mfc-shared/reference/cstringt-class.md)之間的資料錄檢視中的下拉式方塊控制項的編輯控制項的資料和`CString`資料錄檢視相關聯的資料錄集欄位資料成員。  
  
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
 中的控制項識別碼[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *值*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 移動資料時從資料錄集的控制項，此函數會設定下拉式方塊，以完全符合字串中指定的第一個資料列的目前選取範圍*值*。 在從資料錄集傳輸至控制項，如果資料錄集欄位為 NULL，任一選取項目已從下拉式方塊和下拉式方塊的編輯方塊會設為空白。 在從控制項傳輸至資料錄集，如果控制項是空的資料錄集欄位設為 NULL。  
  
 如果您正在使用的 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用 DAO 類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 呼叫`DDX_FieldCBStringExact`會如下所示。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="ddx_fieldcheck"></a>  DDX_FieldCheck  
 `DDX_FieldCheck`函式會管理的傳輸`int`在對話方塊中，核取方塊控制項之間的資料形成檢視或控制項檢視物件和`int`對話方塊、 表單檢視或控制項檢視物件的資料成員。  
  
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
  
 *值*  
 對話方塊、 表單檢視中或用來交換資料的控制項檢視物件的成員變數參考。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 當`DDX_FieldCheck`呼叫時，*值*設為目前狀態的核取方塊控制項，或控制項的狀態會設為*值*，端視傳送的方向。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="ddx_fieldlbindex"></a>  DDX_FieldLBIndex  
 `DDX_FieldLBIndex`函式會同步處理選取的項目在清單方塊控制項中資料錄檢視的索引和`int`資料錄檢視相關聯的資料錄集欄位資料成員。  
  
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
 中的控制項識別碼[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *index*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 移動資料時從資料錄集的控制項，此函數會設定控制項中指定的值為基礎的選取項目*索引*。 在從資料錄集傳輸至控制項，如果資料錄集欄位為 Null，MFC 會設定索引的值為 0。 在從控制項傳輸至資料錄集，如果控制項是空的資料錄集欄位是設定為 0。  
  
 如果您正在使用的 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用 DAO 類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="ddx_fieldlbstring"></a>  DDX_FieldLBString  
 `DDX_FieldLBString`複製資料錄檢視中的清單方塊控制項的目前選取範圍[CString](../../atl-mfc-shared/reference/cstringt-class.md)資料錄檢視相關聯的資料錄集欄位資料成員。  
  
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
 中的控制項識別碼[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *值*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 相反的方向，此函式會將目前的選取範圍開頭的字元所指定的字串中第一個資料列的清單方塊中*值*。 從資料錄集傳輸至控制項，在資料錄集欄位為 Null，如果任何選取項目會移除從清單方塊。 在從控制項傳輸至資料錄集，如果控制項是空的資料錄集欄位設為 Null。  
  
 如果您正在使用的 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用 DAO 類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 呼叫`DDX_FieldLBString`會如下所示。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="ddx_fieldlbstringexact"></a>  DDX_FieldLBStringExact  
 `DDX_FieldLBStringExact`函式會將清單方塊控制項的目前選取範圍複製資料錄檢視中[CString](../../atl-mfc-shared/reference/cstringt-class.md)資料錄檢視相關聯的資料錄集欄位資料成員。  
  
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
 中的控制項識別碼[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *值*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 相反的方向，此函式會將目前的選取範圍完全符合字串中指定的第一個資料列的清單方塊中*值*。 從資料錄集傳輸至控制項，在資料錄集欄位為 Null，如果任何選取項目會移除從清單方塊。 在從控制項傳輸至資料錄集，如果控制項是空的資料錄集欄位設為 Null。  
  
 如果您正在使用的 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用 DAO 類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 呼叫`DDX_FieldLBStringExact`會如下所示。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="ddx_fieldradio"></a>  DDX_FieldRadio  
 `DDX_FieldRadio`函式將以零為起始`int`成員變數的資料錄檢視的資料錄集與資料錄檢視中的選項按鈕群組中的目前選取的選項按鈕。  
  
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
 識別碼的第一個群組中 (樣式**WS_GROUP**) 中的相鄰的選項按鈕控制項的[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *值*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 將從資料錄集欄位傳送到檢視，此函式會開啟*第 n 個*（以零為起始） 的選項按鈕和其他按鈕關閉。 相反的方向，此函式會將資料錄集欄位是目前的 （核取） 的選項按鈕的序號。 在從資料錄集傳輸至控制項，如果資料錄集欄位為 Null，就會選取沒有 按鈕。 在從控制項傳輸至資料錄集，如果已不選取任何控制項，資料錄集欄位設為 Null 若欄位允許的。  
  
 如果您正在使用的 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用 DAO 類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 呼叫`DDX_FieldRadio`會如下所示。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="ddx_fieldscroll"></a>  DDX_FieldScroll  
 `DDX_FieldScroll`函式會同步處理資料錄檢視中的捲軸控制項捲軸位置和`int`與資料錄檢視 （或您選擇將它對應至任何整數變數） 相關聯的資料錄集欄位資料成員。  
  
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
 識別碼的第一個群組中 (樣式**WS_GROUP**) 中的相鄰的選項按鈕控制項的[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *值*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。  
  
### <a name="remarks"></a>備註  
 移動資料時從資料錄集的控制項，此函式設捲軸控制項的捲動位置的值中指定*值*。 在從資料錄集傳輸至控制項，如果資料錄集欄位為 Null，捲軸控制項是設定為 0。 在從控制項傳輸至資料錄集，如果控制項是空的資料錄集欄位的值為 0。  
  
 如果您正在使用的 ODBC 為基礎的類別，請使用第一個版本。 如果您正在使用 DAO 類別，請使用第二個版本。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 呼叫`DDX_FieldScroll`會如下所示。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  

  ## <a name="nameddxfieldslidera--ddxfieldslider"></a>name="ddx_fieldslider"></a>  DDX_FieldSlider
`DDX_FieldSlider`函式會同步處理資料錄檢視中的滑桿控制項捲動方塊位置和`int`與資料錄檢視 （或您選擇將它對應至任何整數變數） 相關聯的資料錄集欄位資料成員。  
   
### <a name="syntax"></a>語法  
  ```
   void AFXAPI DDX_FieldSlider(  
       CDataExchange* pDX,  
       int nIDC,  
       int& value,  
       CRecordset* pRecordset );  

void AFXAPI DDX_FieldSlider(  
     CDataExchange* pDX,  
     int nIDC,  
     int& value,  
     CDaoRecordset* pRecordset );  
```
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `nIDC`  
 滑桿控制項的資源識別碼。  
  
 *值*  
 交換值的參考。 這個參數保留或將用來設定滑桿控制項的目前捲動方塊位置。  
  
 `pRecordset`  
 相關聯的指標`CRecordset`或`CDaoRecordset`交換資料的物件。  
   
### <a name="remarks"></a>備註  
 當從資料錄集的資料移動滑桿中，則此函式會將滑桿的位置中指定的值*值*。 在從資料錄集傳輸至控制項，如果資料錄集欄位為 Null，滑桿控制項的位置會設定為 0。 在從控制項傳輸至資料錄集，如果控制項是空的資料錄集欄位的值為 0。  
  
 `DDX_FieldSlider` 不交換與滑桿控制項能夠設定範圍，而不是只需位置的範圍資訊。  
  
 如果您正在使用的 ODBC 為基礎的類別，請使用函式的第一個覆寫。 使用 DAO 類別中的第二個覆寫。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../dialog-data-exchange-and-validation.md)。 範例和詳細資訊的 DDX`CRecordView`和`CDaoRecordView`欄位，請參閱[資料錄檢視](../../data/record-views-mfc-data-access.md)。 滑桿控制項的相關資訊，請參閱[使用 CSliderCtrl](../using-csliderctrl.md)。  
   
### <a name="example"></a>範例  
 請參閱[DDX_FieldText](#ddx_fieldtext)一般 DDX_Field 範例。 呼叫`DDX_FieldSlider`會如下所示。  
   
### <a name="requirements"></a>需求  
 **標頭：** afxdao.h  
   
### <a name="see-also"></a>另請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
  
##  <a name="ddx_fieldtext"></a>  DDX_FieldText  
 `DDX_FieldText`函式會管理的傳輸`int`，**簡短**，**長**， `DWORD`， [CString](../../atl-mfc-shared/reference/cstringt-class.md)， **float**， **double**， **BOOL**，或**位元組**編輯方塊控制項和資料錄集的欄位資料成員之間的資料。  
  
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
 中的控制項識別碼[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)物件。  
  
 *值*  
 在相關聯的欄位資料成員的參考`CRecordset`或`CDaoRecordset`物件。 值的資料類型取決於哪一個多載版本`DDX_FieldText`您使用。  
  
 `pRecordset`  
 指標[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)交換資料的物件。 此指標可以讓`DDX_FieldText`偵測及設定 Null 值。  
  
### <a name="remarks"></a>備註  
 如[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件`DDX_FieldText`也會管理傳送[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)，和[COleCurrency](../../mfc/reference/colecurrency-class.md)值。 空白的編輯方塊控制項表示 Null 值。 從資料錄集傳輸至控制項，如果資料錄集欄位為 Null，在編輯方塊會設定為空白。 在從控制項傳輸至資料錄集，如果控制項是空的資料錄集欄位設為 Null。  
  
 使用與版本[CRecordset](../../mfc/reference/crecordset-class.md)參數，如果您正在使用的 ODBC 為基礎的類別。 使用與版本[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)參數，如果您正在使用的 DAO 架構類別。  
  
 如需有關 DDX 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 範例和詳細資訊的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)欄位，請參閱文章[資料錄檢視](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>範例  
 下列`DoDataExchange`函式[CRecordView](../../mfc/reference/crecordview-class.md)包含`DDX_FieldText`函式呼叫的三種資料類型：`IDC_COURSELIST`是下拉式方塊; 其他兩個控制項為編輯方塊。 DAO 程式設計*m_pSet*參數是指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 [!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]  

  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
    
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)
