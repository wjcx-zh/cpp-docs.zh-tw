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
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e53260457470ef75ac706779cea323aa5b73da2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="property-pages-mfc"></a>屬性頁 (MFC)
屬性頁來檢視及編輯支援對話方塊資料交換 (DDX) 為基礎的資料對應機制的可自訂的圖形化介面中顯示特定的 OLE 控制項屬性的目前值。  
  
 此資料對應機制會將屬性頁面會控制對應至 OLE 控制項的個別屬性。 控制項屬性的值會反映狀態或屬性頁面控制項的內容。 屬性頁控制項和屬性之間的對應由指定**DDP_**屬性頁中的函式呼叫`DoDataExchange`成員函式。 下列是一份**DDP_**交換資料，使用您的控制項的屬性頁輸入的函式：  
  
### <a name="property-page-data-transfer"></a>屬性頁資料傳輸  
  
|||  
|-|-|  
|[DDP_CBIndex](#ddp_cbindex)|連結控制項的屬性與下拉式方塊中選取的字串索引。|  
|[DDP_CBString](#ddp_cbstring)|連結控制項的屬性與下拉式方塊中選取的字串。 選取的字串可以具有相同屬性的值為字母開頭，但不需要完全相符。|  
|[DDP_CBStringExact](#ddp_cbstringexact)|連結控制項的屬性與下拉式方塊中選取的字串。 選取的字串和屬性的字串值必須完全相符。|  
|[DDP_Check](#ddp_check)|核取方塊控制項的內容控制項的屬性頁中的連結。|  
|[DDP_LBIndex](#ddp_lbindex)|連結控制項的屬性與清單方塊中選取的字串索引。|  
|[DDP_LBString](#ddp_lbstring)|連結控制項的屬性清單方塊中選取的字串。 選取的字串可以具有相同屬性的值為字母開頭，但需要不一定要完全符合。|  
|[DDP_LBStringExact](#ddp_lbstringexact)|連結控制項的屬性清單方塊中選取的字串。 選取的字串和屬性的字串值必須完全相符。|  
|[DDP_PostProcessing](#ddp_postprocessing)|完成從您的控制項屬性值的傳輸。|  
|[DDP_Radio](#ddp_radio)|在控制項的屬性頁面中的控制項屬性的選項按鈕群組的連結。|  
|[DDP_Text](#ddp_text)|連結控制項的屬性頁，以將控制項的屬性中的控制項。 此函式會處理多種不同類型的屬性，例如**double**，**簡短**， `BSTR`，和**長**。|  
  
 如需有關`DoDataExchange`函式和屬性頁，請參閱文章[ActiveX 控制項： 屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。  
  
 下列是用來建立及管理的 OLE 控制項屬性頁的巨集的清單：  
  
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
 呼叫此函式在屬性頁的`DoDataExchange`同步處理之字串屬性值與屬性頁上的下拉式方塊中目前選取的函式。  
  
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
 要與所指定的下拉式方塊字串交換的控制項屬性的屬性名稱`id`。  
  
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
 要與所指定的下拉式方塊字串交換的控制項屬性的屬性名稱`id`。  
  
### <a name="remarks"></a>備註  
 應該在對應的 `DDX_CBStringExact` 函式呼叫之前呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_check"></a>DDP_Check  
 呼叫此函式在屬性頁的`DoDataExchange`與相關聯的屬性頁面 核取方塊控制項同步處理的屬性值的函式。  
  
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
 與所指定的控制項屬性的核取方塊控制項的資源識別碼相關聯`pszPropName`。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 要與所指定的核取方塊控制項交換的控制項屬性的屬性名稱`id`。  
  
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
 資源識別碼的清單方塊所指定的控制項屬性相關聯的控制項`pszPropName`。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 要與清單方塊中指定的字串以交換的控制項屬性的屬性名稱`id`。  
  
### <a name="remarks"></a>備註  
 應該在對應的 `DDX_LBIndex` 函式呼叫之前呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_lbstring"></a>DDP_LBString  
 呼叫此函式在屬性頁的`DoDataExchange`同步處理之字串屬性值與屬性頁上的清單方塊中目前選取的函式。  
  
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
 資源識別碼的清單方塊所指定的控制項屬性相關聯的控制項`pszPropName`。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 要與清單方塊中指定的字串以交換的控制項屬性的屬性名稱`id`。  
  
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
 資源識別碼的清單方塊所指定的控制項屬性相關聯的控制項`pszPropName`。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 要與清單方塊中指定的字串以交換的控制項屬性的屬性名稱`id`。  
  
### <a name="remarks"></a>備註  
 應該在對應的 `DDX_LBStringExact` 函式呼叫之前呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_postprocessing"></a>DDP_PostProcessing  
 呼叫此函式在屬性頁的`DoDataExchange`函式，來完成屬性值可從 [屬性] 頁面傳輸至您的控制項，在儲存屬性值時。  
  
```   
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指向 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
### <a name="remarks"></a>備註  
 所有的資料交換函式完成之後，應該呼叫此函式。 例如:   
  
 [!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_radio"></a>DDP_Radio  
 呼叫此函式在控制項的`DoPropExchange`與相關聯的屬性頁面的選項按鈕控制項同步處理的屬性值的函式。  
  
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
 要與所指定的選項按鈕控制項交換的控制項屬性的屬性名稱`id`。  
  
### <a name="remarks"></a>備註  
 應該在對應的 `DDX_Radio` 函式呼叫之前呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="ddp_text"></a>DDP_Text  
 呼叫此函式在控制項的`DoDataExchange`與相關聯的屬性頁控制項同步處理的屬性值的函式。  
  
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
 所指定的控制項屬性相關聯控制項的資源識別碼`pszPropName`。  
  
 `member`  
 與 `id` 指定的屬性頁控制項和 `pszPropName` 指定的屬性相關聯的成員變數。  
  
 `pszPropName`  
 要與所指定的控制項交換的控制項屬性的屬性名稱`id`。  
  
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
 為屬性指定頁的控制項類別名稱。  
  
 *count*  
 控制項類別所使用的屬性頁數目。  
  
### <a name="remarks"></a>備註  
 在定義類別的成員函式的實作 (.cpp) 檔案，啟動 屬性頁清單與`BEGIN_PROPPAGEIDS`巨集，然後針對每個屬性頁中，加入巨集項目，並完成屬性頁面清單與`END_PROPPAGEIDS`巨集。  
  
 如需有關屬性頁的詳細資訊，請參閱文章[ActiveX 控制項： 屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="end_proppageids"></a>END_PROPPAGEIDS  
 結束屬性頁 ID 清單的定義。  
  
```   
END_PROPPAGEIDS(class_name)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 擁有屬性頁的控制項類別名稱。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="proppageid"></a>PROPPAGEID  
 將 OLE 控制項使用的屬性頁。  
  
```   
PROPPAGEID(clsid)   
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 屬性頁的唯一類別 ID。  
  
### <a name="remarks"></a>備註  
 所有`PROPPAGEID`必須放置於巨集之間`BEGIN_PROPPAGEIDS`和`END_PROPPAGEIDS`巨集，在您的控制項實作檔。  

### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
    
## <a name="see-also"></a>請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)
