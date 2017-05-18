---
title: "CDBVariant 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDBVariant
- AFXDB/CDBVariant
- AFXDB/CDBVariant::CDBVariant
- AFXDB/CDBVariant::Clear
- AFXDB/CDBVariant::m_dwType
- AFXDB/CDBVariant::m_boolVal
- AFXDB/CDBVariant::m_chVal
- AFXDB/CDBVariant::m_dblVal
- AFXDB/CDBVariant::m_fltVal
- AFXDB/CDBVariant::m_iVal
- AFXDB/CDBVariant::m_lVal
- AFXDB/CDBVariant::m_pbinary
- AFXDB/CDBVariant::m_pdate
- AFXDB/CDBVariant::m_pstring
- AFXDB/CDBVariant::m_pstringA
- AFXDB/CDBVariant::m_pstringW
dev_langs:
- C++
helpviewer_keywords:
- CDBVariant class
- Variant data types, ODBC
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
caps.latest.revision: 21
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 930115ce4fe673e82a447ab1d90c260fe2b941d6
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cdbvariant-class"></a>CDBVariant 類別
表示 MFC ODBC 類別的 Variant 資料類型。  
  
## <a name="syntax"></a>語法  
  
```  
class CDBVariant  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CDBVariant::CDBVariant](#cdbvariant)|建構 `CDBVariant` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDBVariant::Clear](#clear)|清除`CDBVariant`物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDBVariant::m_dwType](#m_dwtype)|包含目前儲存的值的資料型別。 輸入 `DWORD`。|  
  
### <a name="public-union-members"></a>公用的等位成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDBVariant::m_boolVal](#m_boolval)|包含型別的值**BOOL**。|  
|[CDBVariant::m_chVal](#m_chval)|包含型別的值`unsigned char`。|  
|[CDBVariant::m_dblVal](#m_dblval)|包含型別的值**雙**。|  
|[CDBVariant::m_fltVal](#m_fltval)|包含型別的值**float**。|  
|[CDBVariant::m_iVal](#m_ival)|包含型別的值**簡短**。|  
|[CDBVariant::m_lVal](#m_lval)|包含型別的值**長**。|  
|[CDBVariant::m_pbinary](#m_pbinary)|包含型別的物件的指標`CLongBinary`。|  
|[CDBVariant::m_pdate](#m_pdate)|包含型別的物件的指標**TIMESTAMP_STRUCT**。|  
|[CDBVariant::m_pstring](#m_pstring)|包含型別的物件的指標`CString`。|  
|[CDBVariant::m_pstringA](#m_pstringa)|儲存的指標 ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。|  
|[CDBVariant::m_pstringW](#m_pstringw)|儲存的指標寬[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。|  
  
## <a name="remarks"></a>備註  
 `CDBVariant`沒有基底類別。  
  
 `CDBVariant`類似於[COleVariant](../../mfc/reference/colevariant-class.md); 不過，`CDBVariant`不會使用 OLE。 `CDBVariant`可讓您儲存值，而不需擔心值的資料類型。 `CDBVariant`會追蹤目前的值等位中儲存的資料型別。  
  
 類別[CRecordset](../../mfc/reference/crecordset-class.md)利用`CDBVariant`三個成員函式中的物件︰ `GetFieldValue`， `GetBookmark`，和`SetBookmark`。 例如，`GetFieldValue`可讓您以動態方式提取資料行中的資料。 因為資料行的資料型別可能不知道在執行階段，`GetFieldValue`使用`CDBVariant`物件來儲存資料行的資料。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CDBVariant`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  
  
##  <a name="cdbvariant"></a>CDBVariant::CDBVariant  
 建立 NULL`CDBVariant`物件。  
  
```  
CDBVariant();
```  
  
### <a name="remarks"></a>備註  
 設定[m_dwType](#m_dwtype)資料成員，才能**DBVT_NULL**。  
  
##  <a name="clear"></a>CDBVariant::Clear  
 呼叫此成員函式，以清除`CDBVariant`物件。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
 如果值[m_dwType](#m_dwtype)資料成員是**DBVT_DATE**， **DBVT_STRING**，或**DBVT_BINARY**，**清除**釋放等位的指標成員相關聯的記憶體。 **清除**設定`m_dwType`至**DBVT_NULL**。  
  
 `CDBVariant`解構函式呼叫**清除**。  
  
##  <a name="m_boolval"></a>CDBVariant::m_boolVal  
 儲存的型別值**BOOL**。  
  
### <a name="remarks"></a>備註  
 **M_boolVal**資料成員所屬的等位。 存取之前**m_boolVal**，值會先檢查[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為**DBVT_BOOL**，然後**m_boolVal**將包含有效的值; 否則存取**m_boolVal**會產生不可靠的結果。  
  
##  <a name="m_chval"></a>CDBVariant::m_chVal  
 儲存的型別值`unsigned char`。  
  
### <a name="remarks"></a>備註  
 **M_chVal**資料成員所屬的等位。 存取之前**m_chVal**，值會先檢查[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為**DBVT_UCHAR**，然後**m_chVal**包含有效的值; 否則存取**m_chVal**會產生不可靠的結果。  
  
##  <a name="m_dblval"></a>CDBVariant::m_dblVal  
 儲存的型別值**雙**。  
  
### <a name="remarks"></a>備註  
 **M_dblVal**資料成員所屬的等位。 存取之前**m_dblVal**，值會先檢查[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為**DBVT_DOUBLE**，然後**m_dblVal**包含有效的值; 否則存取**m_dblVal**會產生不可靠的結果。  
  
##  <a name="m_dwtype"></a>CDBVariant::m_dwType  
 此資料成員包含目前儲存在中的值的資料型別`CDBVariant`物件的聯集的資料成員。  
  
### <a name="remarks"></a>備註  
 才能存取這個聯集，您必須檢查的值`m_dwType`才能判斷存取的等位資料成員。 下表列出可能的值為`m_dwType`和相對應的等位資料成員。  
  
|m_dwType|等位資料成員|  
|---------------|-----------------------|  
|**DBVT_NULL**|不等位的成員僅適用於存取項目。|  
|**DBVT_BOOL**|[m_boolVal](#m_boolval)|  
|**DBVT_UCHAR**|[m_chVal](#m_chval)|  
|**DBVT_SHORT**|[m_iVal](#m_ival)|  
|**DBVT_LONG**|[m_lVal](#m_lval)|  
|**DBVT_SINGLE**|[m_fltVal](#m_fltval)|  
|**DBVT_DOUBLE**|[m_dblVal](#m_dblval)|  
|**DBVT_DATE**|[m_pdate](#m_pdate)|  
|**DBVT_STRING**|[m_pstring](#m_pstring)|  
|**DBVT_BINARY**|[m_pbinary](#m_pbinary)|  
|**DBVT_ASTRING**|[m_pstringA](#m_pstringa)|  
|**DBVT_WSTRING**|[m_pstringW](#m_pstringw)|  
  
##  <a name="m_fltval"></a>CDBVariant::m_fltVal  
 儲存的型別值**float**。  
  
### <a name="remarks"></a>備註  
 **M_fltVal**資料成員所屬的等位。 存取之前**m_fltVal**，值會先檢查[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為**DBVT_SINGLE**，然後**m_fltVal**包含有效的值; 否則存取**m_fltVal**會產生不可靠的結果。  
  
##  <a name="m_ival"></a>CDBVariant::m_iVal  
 儲存的型別值**簡短**。  
  
### <a name="remarks"></a>備註  
 **M_iVal**資料成員所屬的等位。 存取之前**m_iVal**，值會先檢查[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為**DBVT_SHORT**，然後**m_iVal**包含有效的值; 否則存取**m_iVal**會產生不可靠的結果。  
  
##  <a name="m_lval"></a>CDBVariant::m_lVal  
 儲存的型別值**長**。  
  
### <a name="remarks"></a>備註  
 **M_lVal**資料成員所屬的等位。 存取之前**m_lVal**，值會先檢查[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為**DBVT_LONG**，然後**m_lVal**包含有效的值; 否則存取**m_lVal**會產生不可靠的結果。  
  
##  <a name="m_pbinary"></a>CDBVariant::m_pbinary  
 儲存型別的物件的指標[CLongBinary](../../mfc/reference/clongbinary-class.md)。  
  
### <a name="remarks"></a>備註  
 **M_pbinary**資料成員所屬的等位。 存取之前**m_pbinary**，值會先檢查[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為**DBVT_BINARY**，然後**m_pbinary**包含有效的指標; 否則存取**m_pbinary**會產生不可靠的結果。  
  
##  <a name="m_pdate"></a>CDBVariant::m_pdate  
 儲存型別的物件的指標**TIMESTAMP_STRUCT**。  
  
### <a name="remarks"></a>備註  
 **M_pdate**資料成員所屬的等位。 存取之前**m_pdate**，值會先檢查[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為**DBVT_DATE**，然後**m_pdate**包含有效的指標; 否則存取**m_pdate**會產生不可靠的結果。  
  
 如需詳細資訊**TIMESTAMP_STRUCT**資料類型，請參閱主題[C 資料型別](https://msdn.microsoft.com/library/ms714556.aspx)中的附錄 D *ODBC 程式設計人員參考*中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="m_pstring"></a>CDBVariant::m_pstring  
 儲存型別的物件的指標[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>備註  
 **M_pstring**資料成員所屬的等位。 存取之前**m_pstring**，值會先檢查[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為**DBVT_STRING**，然後**m_pstring**包含有效的指標; 否則存取**m_pstring**會產生不可靠的結果。  
  
##  <a name="m_pstringa"></a>CDBVariant::m_pstringA  
 儲存的指標 ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。  
  
### <a name="remarks"></a>備註  
 **M_pstringA**資料成員所屬的等位。 存取之前**m_pstringA**，值會先檢查[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為**DBVT_ASTRING**，然後**m_pstringA**包含有效的指標; 否則存取**m_pstringA**會產生不可靠的結果。  
  
##  <a name="m_pstringw"></a>CDBVariant::m_pstringW  
 儲存的指標寬[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。  
  
### <a name="remarks"></a>備註  
 **M_pstringW**資料成員所屬的等位。 存取之前**m_pstringW**，值會先檢查[CDBVariant::m_dwType](#m_dwtype)。 如果`m_dwType`設為**DBVT_WSTRING**，然後**m_pstringW**包含有效的指標; 否則存取**m_pstringW**會產生不可靠的結果。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)

