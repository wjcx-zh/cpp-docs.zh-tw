---
title: CSettingsStoreSP 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1852f4e280fa49a2436c421d4669e9d735d66c3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="csettingsstoresp-class"></a>CSettingsStoreSP 類別
`CSettingsStoreSP`類別是協助程式類別可讓您建立的執行個體[CSettingsStore 類別](../../mfc/reference/csettingsstore-class.md)。  
  
## <a name="syntax"></a>語法  
  
```  
class CSettingsStoreSP  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSettingsStoreSP::CSettingsStoreSP](#csettingsstoresp)|建構 `CSettingsStoreSP` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSettingsStoreSP::Create](#create)|建立衍生自類別的執行個體`CSettingsStore`。|  
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|設定執行階段類別。 `Create`方法來判斷哪些類別的物件，以建立會使用執行階段類別。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|`m_dwUserData`|自訂使用者資料儲存在`CSettingsStoreSP`物件。 您提供的建構函式中的這個資料`CSettingsStoreSP`物件。|  
|`m_pRegistry`|`CSettingsStore`-衍生物件`Create`方法會建立。|  
  
## <a name="remarks"></a>備註  
 您可以使用`CSettingsStoreSP`重新導向到其他位置，例如 XML 檔案或資料庫的所有 MFC 登錄作業的類別。 若要執行這項操作，請依照下列步驟執行：  
  
1.  建立類別 (例如`CMyStore`) 並從它衍生`CSettingsStore`。  
  
2.  使用[DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)和[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)巨集與您的自訂`CSettingsStore`以啟用動態建立的類別。  
  
3.  覆寫虛擬函式，並實作`Read`和`Write`中自訂類別的函式。 實作任何其他功能來讀取及寫入資料至您想要的位置。  
  
4.  在您的應用程式呼叫`CSettingsStoreSP::SetRuntimeClass`並傳入的指標[CRuntimeClass 結構](../../mfc/reference/cruntimeclass-structure.md)取自您的類別。  
  
 每當架構通常會存取登錄，它會立即動態具現化您的自訂類別，並用來讀取或寫入資料。  
  
 `CSettingsStoreSP::SetRuntimeClass` 使用全域靜態變數。 因此，只有一個自訂存放區可一次。  
  
## <a name="requirements"></a>需求  
 **標頭：** afxsettingsstore.h  
  
##  <a name="create"></a>  CSettingsStoreSP::Create  
 建立衍生自物件的新執行個體[CSettingsStore 類別](../../mfc/reference/csettingsstore-class.md)。  
  
```  
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bAdmin`  
 布林值參數會決定是否`CSettingsStore`系統管理員模式中建立物件。  
  
 [輸入] `bReadOnly`  
 布林值參數會決定是否`CSettingsStore`建立物件的唯讀存取權。  
  
### <a name="return-value"></a>傳回值  
 新建立的參考`CSettingsStore`物件。  
  
### <a name="remarks"></a>備註  
 您可以使用此方法[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)來判斷何種物件`CSettingsStoreSP::Create`會建立。 根據預設，這個方法會建立`CSettingsStore`物件。  
  
 如果您建立`CSettingsStore`物件在系統管理員模式中，所有存取登錄的預設位置是 HKEY_LOCAL_MACHINE。 否則，所有存取登錄的預設位置是 HKEY_CURRENT_USER。  
  
 如果`bAdmin`是`TRUE`，應用程式必須具備系統管理權限。 否則，它將會失敗時嘗試存取登錄。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`Create`方法`CSettingsStoreSP`類別。  
  
 [!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]  
  
##  <a name="csettingsstoresp"></a>  CSettingsStoreSP::CSettingsStoreSP  
 建構[CSettingsStoreSP 類別](../../mfc/reference/csettingsstoresp-class.md)物件。  
  
```  
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `dwUserData`  
 使用者定義資料的`CSettingsStoreSP`物件存放區。  
  
### <a name="remarks"></a>備註  
 `CSettingsStoreSP`物件會儲存從資料`dwUserData`受保護的成員變數中`m_dwUserData`。  
  
##  <a name="setruntimeclass"></a>  CSettingsStoreSP::SetRuntimeClass  
 設定執行階段類別。 此方法[CSettingsStoreSP::Create](#create)會使用執行階段類別，來判斷要建立的物件類型。  
  
```  
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pRTI`  
 從衍生類別的執行階段類別資訊指標[CSettingsStore 類別](../../mfc/reference/csettingsstore-class.md)。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果登錄成功。，`FALSE`如果所識別的類別`pRTI`不衍生自`CSettingsStore`。  
  
### <a name="remarks"></a>備註  
 您可以使用[CSettingsStoreSP 類別](../../mfc/reference/csettingsstoresp-class.md)衍生類別，從`CSettingsStore`。 使用方法`SetRuntimeClass`如果您想要建立的自訂類別，衍生自物件`CSettingsStore`。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CSettingsStore 類別](../../mfc/reference/csettingsstore-class.md)
