---
title: "屬性頁 (MFC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages, global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
caps.latest.revision: 14
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 50888697fe01d3a84d9aa4c6f5f92926e4681535
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="property-pages-mfc"></a>屬性頁 (MFC)
屬性頁檢視和編輯支援對話資料交換 (DDX) 為基礎的資料對應機制的可自訂的圖形化介面中顯示 OLE 控制項的特定屬性的目前值。  
  
 這項資料對應機制會對應至個別的 OLE 控制項屬性的屬性頁面控制項。 控制項屬性的值反映的狀態或屬性頁控制項的內容。 屬性頁控制項和屬性之間的對應由**DDP_**屬性頁中的函數呼叫`DoDataExchange`成員函式。 下列是一份**DDP_**交換使用屬性頁，控制項的輸入資料的函式︰  
  
### <a name="property-page-data-transfer"></a>屬性頁資料傳輸  
  
|||  
|-|-|  
|[DDP_CBIndex](#ddp_cbindex)|連結控制項的屬性與下拉式方塊中選取的字串的索引。|  
|[DDP_CBString](#ddp_cbstring)|連結控制項的屬性與下拉式方塊中選取的字串。 選取的字串都可以使用做為屬性值的相同字母開頭，但不需要一定要完全符合。|  
|[DDP_CBStringExact](#ddp_cbstringexact)|連結控制項的屬性與下拉式方塊中選取的字串。 選取的字串和屬性的字串值必須完全相符。|  
|[DDP_Check](#ddp_check)|核取方塊控制項的屬性與控制項的屬性頁中的連結。|  
|[DDP_LBIndex](#ddp_lbindex)|連結與控制項的屬性清單方塊中選取的字串的索引。|  
|[DDP_LBString](#ddp_lbstring)|連結與控制項的屬性清單方塊中選取的字串。 選取的字串都可以使用做為屬性值的相同字母開頭，但需要完全符合它。|  
|[DDP_LBStringExact](#ddp_lbstringexact)|連結與控制項的屬性清單方塊中選取的字串。 選取的字串和屬性的字串值必須完全相符。|  
|[DDP_PostProcessing](#ddp_postprocessing)|完成從控制項傳送的屬性值。|  
|[DDP_Radio](#ddp_radio)|與控制項屬性的控制項的屬性頁中的選項按鈕群組的連結。|  
|[DDP_Text](#ddp_text)|與控制項屬性的控制項的屬性頁中的控制項的連結。 此函式會處理許多不同類型的屬性，例如**雙**，**簡短**， `BSTR`，和**長**。|  
  
 如需詳細資訊`DoDataExchange`函式和屬性頁，請參閱文章[ActiveX 控制項︰ 屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。  
  
 下列是用來建立及管理 OLE 控制項的屬性頁的巨集的清單︰  
  
### <a name="property-pages"></a>屬性頁  
  
|||  
|-|-|  
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|開始屬性頁 Id 的清單。|  
|[END_PROPPAGEIDS](#end_proppageids)|結束屬性頁 Id 的清單。|  
|[PROPPAGEID](#proppageid)|宣告屬性頁的控制項類別。|  
  
##  <a name="ddp_cbindex"></a>DDP_CBIndex  
 呼叫您屬性頁的 `DoDataExchange` 函式中的這個函式，來同步處理整數屬性的值與在屬性頁中下拉式方塊裡目前選取範圍的索引。  
  
```   
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,  
    int id,  
    int& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `id`  
 與 `pszPropName` 指定的控制項屬性相關聯的下拉式方塊控制項的資源 ID。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 要與 `id` 指定的下拉式方塊控制項交換的控制項屬性的屬性名稱。  
  
### <a name="remarks"></a>備註  
 應該在對應的 `DDX_CBIndex` 函式呼叫之前呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_cbstring"></a>DDP_CBString  
 呼叫此函式在屬性頁的`DoDataExchange`屬性頁上的下拉式方塊目前的選取範圍與同步處理的字串屬性值的函式。  
  
```  
void AFXAPI DDP_CBString(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `id`  
 與 `pszPropName` 指定的控制項屬性相關聯的下拉式方塊控制項的資源 ID。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 與下拉式方塊中指定的字串以交換的控制項屬性的屬性名稱`id`。  
  
### <a name="remarks"></a>備註  
 應該在對應的 `DDX_CBString` 函式呼叫之前呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_cbstringexact"></a>DDP_CBStringExact  
 呼叫此函式在屬性頁的`DoDataExchange`函式來同步處理完全符合目前的選取範圍，在 [屬性] 頁面上的下拉式方塊中為字串屬性的值。  
  
```  
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `id`  
 與 `pszPropName` 指定的控制項屬性相關聯的下拉式方塊控制項的資源 ID。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 與下拉式方塊中指定的字串以交換的控制項屬性的屬性名稱`id`。  
  
### <a name="remarks"></a>備註  
 應該在對應的 `DDX_CBStringExact` 函式呼叫之前呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_check"></a>DDP_Check  
 呼叫此函式在屬性頁的`DoDataExchange`函式相關聯的屬性頁 核取方塊控制項與同步處理屬性的值。  
  
```   
void AFXAPI DDP_Check(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCSTR pszPropName);
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `id`  
 與所指定的控制項屬性相關聯的核取方塊控制項的資源識別碼`pszPropName`。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 與所指定的核取方塊控制項交換的控制項屬性的屬性名稱`id`。  
  
### <a name="remarks"></a>備註  
 應該在對應的 `DDX_Check` 函式呼叫之前呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_lbindex"></a>DDP_LBIndex  
 呼叫此函式在屬性頁的`DoDataExchange`函式來同步處理整數屬性的值與目前的選取範圍，在 [屬性] 頁面上的清單方塊中的索引。  
  
```   
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,  
    int id,  
    int& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `id`  
 資源的清單方塊控制項的 ID 與所指定的控制項屬性相關聯`pszPropName`。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 要與清單方塊中指定的字串以交換之控制項屬性的屬性名稱`id`。  
  
### <a name="remarks"></a>備註  
 應該在對應的 `DDX_LBIndex` 函式呼叫之前呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_lbstring"></a>DDP_LBString  
 呼叫此函式在屬性頁的`DoDataExchange`屬性頁上的清單方塊中目前的選取與同步處理的字串屬性值的函式。  
  
```   
void AFXAPI DDP_LBString(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `id`  
 資源的清單方塊控制項的 ID 與所指定的控制項屬性相關聯`pszPropName`。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 要與清單方塊中指定的字串以交換之控制項屬性的屬性名稱`id`。  
  
### <a name="remarks"></a>備註  
 應該在對應的 `DDX_LBString` 函式呼叫之前呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_lbstringexact"></a>DDP_LBStringExact  
 呼叫此函式在屬性頁的`DoDataExchange`函式來同步處理完全符合目前的選取範圍，在 [屬性] 頁面上的清單方塊中為字串屬性的值。  
  
```   
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `id`  
 資源的清單方塊控制項的 ID 與所指定的控制項屬性相關聯`pszPropName`。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 要與清單方塊中指定的字串以交換之控制項屬性的屬性名稱`id`。  
  
### <a name="remarks"></a>備註  
 應該在對應的 `DDX_LBStringExact` 函式呼叫之前呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_postprocessing"></a>DDP_PostProcessing  
 呼叫此函式在屬性頁的`DoDataExchange`函式完成時儲存屬性值的屬性值可從 [屬性] 頁面上傳送到您的控制項。  
  
```   
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
### <a name="remarks"></a>備註  
 所有的資料交換函式完成後，應該呼叫此函式。 例如:   
  
 [!code-cpp[NVC_MFCAxCtl #&15;](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_radio"></a>DDP_Radio  
 呼叫此函式在控制項的`DoPropExchange`同步處理相關聯的屬性頁面的選項按鈕控制項的屬性值的函式。  
  
```   
void AFXAPI DDP_Radio(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `id`  
 資源識別碼的選項按鈕控制項所指定的控制項屬性相關聯`pszPropName`。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 與所指定的選項按鈕控制項交換的控制項屬性的屬性名稱`id`。  
  
### <a name="remarks"></a>備註  
 應該在對應的 `DDX_Radio` 函式呼叫之前呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_text"></a>DDP_Text  
 呼叫此函式在控制項的`DoDataExchange`函式相關聯的屬性頁控制項與同步處理屬性的值。  
  
```   
void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    BYTE & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    UINT & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    long & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    DWORD & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    float & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    double & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    CString & member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 `id`  
 控制項所指定的控制項屬性相關聯的資源識別碼`pszPropName`。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 所指定的控制項與交換的控制項屬性的屬性名稱`id`。  
  
### <a name="remarks"></a>備註  
 應該在對應的 `DDX_Text` 函式呼叫之前呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS  
 開始您的控制項屬性頁 Id 清單的定義。  
  
```   
BEGIN_PROPPAGEIDS(class_name,  count)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 為屬性指定頁的控制項類別的名稱。  
  
 *count*  
 Control 類別所使用的屬性頁數目。  
  
### <a name="remarks"></a>備註  
 在定義類別成員函式的實作 (.cpp) 檔案，啟動 屬性頁清單與`BEGIN_PROPPAGEIDS`巨集，然後針對每個屬性頁中，新增巨集項目，並完成屬性頁面清單與`END_PROPPAGEIDS`巨集。  
  
 如需有關屬性頁的詳細資訊，請參閱文章[ActiveX 控制項︰ 屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="end_proppageids"></a>END_PROPPAGEIDS  
 定義屬性頁面識別碼清單的結尾。  
  
```   
END_PROPPAGEIDS(class_name)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 擁有 [屬性] 頁面上的控制項類別的名稱。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="proppageid"></a>PROPPAGEID  
 將您的 OLE 控制項使用的屬性頁。  
  
```   
PROPPAGEID(clsid)   
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 屬性頁的唯一類別 ID。  
  
### <a name="remarks"></a>備註  
 所有`PROPPAGEID`巨集必須位於`BEGIN_PROPPAGEIDS`和`END_PROPPAGEIDS`您的控制項實作檔中的巨集。  

### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
    
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

