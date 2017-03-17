---
title: "COleDispatchDriver 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDispatchDriver
- AFXDISP/COleDispatchDriver
- AFXDISP/COleDispatchDriver::COleDispatchDriver
- AFXDISP/COleDispatchDriver::AttachDispatch
- AFXDISP/COleDispatchDriver::CreateDispatch
- AFXDISP/COleDispatchDriver::DetachDispatch
- AFXDISP/COleDispatchDriver::GetProperty
- AFXDISP/COleDispatchDriver::InvokeHelper
- AFXDISP/COleDispatchDriver::ReleaseDispatch
- AFXDISP/COleDispatchDriver::SetProperty
- AFXDISP/COleDispatchDriver::m_bAutoRelease
- AFXDISP/COleDispatchDriver::m_lpDispatch
dev_langs:
- C++
helpviewer_keywords:
- COleDispatchDriver class
- Automation clients, implementing Automation
- OLE dispatch interface
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 51fc2064e2f4b51b4f4328afb03920dab27ef74b
ms.lasthandoff: 02/24/2017

---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver 類別
實作 OLE Automation 的用戶端。  
  
## <a name="syntax"></a>語法  
  
```  
class COleDispatchDriver  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDispatchDriver::COleDispatchDriver](#coledispatchdriver)|建構 `COleDispatchDriver` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|附加`IDispatch`連接`COleDispatchDriver`物件。|  
|[COleDispatchDriver::CreateDispatch](#createdispatch)|建立`IDispatch`連線，並將它附加`COleDispatchDriver`物件。|  
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|卸離`IDispatch`連線，但未釋放 mutex。|  
|[COleDispatchDriver::GetProperty](#getproperty)|取得自動化屬性。|  
|[COleDispatchDriver::InvokeHelper](#invokehelper)|呼叫自動化方法的協助程式。|  
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|版本`IDispatch`連線。|  
|[COleDispatchDriver::SetProperty](#setproperty)|設定自動化屬性。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDispatchDriver::operator =](#operator_eq)|複製到來源值`COleDispatchDriver`物件。|  
|[COleDispatchDriver::operator LPDISPATCH](#operator_lpdispatch)|存取基礎`IDispatch`指標。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|指定是否要釋放`IDispatch`期間`ReleaseDispatch`或物件解構。|  
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|指出指標`IDispatch`介面附加至這個`COleDispatchDriver`。|  
  
## <a name="remarks"></a>備註  
 `COleDispatchDriver`沒有基底類別。  
  
 OLE 分派介面可存取物件的方法和屬性。 成員函式的`COleDispatchDriver`附加、 卸離、 建立和發行類型的分派連線`IDispatch`。 其他成員函式使用變數引數清單，以簡化呼叫**Excepinfo**。  
  
 這個類別可以直接使用，但它通常由只加入類別精靈所建立的類別。 當您匯入類型程式庫建立新的 c + + 類別時，將新的類別衍生自`COleDispatchDriver`。  
  
 如需有關使用`COleDispatchDriver`，請參閱下列文章︰  
  
- [Automation 用戶端](../../mfc/automation-clients.md)  
  
- [Automation 伺服程式](../../mfc/automation-servers.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `COleDispatchDriver`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  
  
##  <a name="attachdispatch"></a>COleDispatchDriver::AttachDispatch  
 呼叫 `AttachDispatch` 成員函式可將 `IDispatch` 指標附加至 `COleDispatchDriver` 物件。 如需詳細資訊，請參閱[實作 IDispatch 介面](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)。  
  
```  
void AttachDispatch(
        LPDISPATCH lpDispatch,  
        BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `lpDispatch`  
 要附加至 `IDispatch` 物件的 OLE `COleDispatchDriver` 物件指標。  
  
 `bAutoRelease`  
 指定當這個物件移出範圍時，是否要釋放此分派。  
  
### <a name="remarks"></a>備註  
 這個函式會釋放已附加至 `IDispatch` 物件的任何 `COleDispatchDriver` 指標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&3;](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]  
  
##  <a name="coledispatchdriver"></a>COleDispatchDriver::COleDispatchDriver  
 建構 `COleDispatchDriver` 物件。  
  
```  
COleDispatchDriver();  
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);  
  COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>參數  
 `lpDispatch`  
 要附加至 `IDispatch` 物件的 OLE `COleDispatchDriver` 物件指標。  
  
 `bAutoRelease`  
 指定當這個物件移出範圍時，是否要釋放此分派。  
  
 `dispatchSrc`  
 參考到現有`COleDispatchDriver`物件。  
  
### <a name="remarks"></a>備註  
 表單`COleDispatchDriver`( `LPDISPATCH``lpDispatch`， **BOOL**`bAutoRelease` = **TRUE**) 連接[IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)介面。  
  
 表單`COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) 複製現有`COleDispatchDriver`物件，並遞增參考計數。  
  
 表單`COleDispatchDriver`（） 會建立`COleDispatchDriver`物件，但不會連線`IDispatch`介面。 使用之前`COleDispatchDriver`（不含引數），您應該連接`IDispatch`它使用[COleDispatchDriver::CreateDispatch](#createdispatch)或[COleDispatchDriver::AttachDispatch](#attachdispatch)。 如需詳細資訊，請參閱[實作 IDispatch 介面](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)。  
  
### <a name="example"></a>範例  
  請參閱範例[COleDispatchDriver::CreateDispatch](#createdispatch)。  
  
##  <a name="createdispatch"></a>COleDispatchDriver::CreateDispatch  
 建立[IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)介面物件，並將它附加`COleDispatchDriver`物件。  
  
```  
BOOL CreateDispatch(
        REFCLSID clsid,  
        COleException* pError = NULL);

 
BOOL CreateDispatch(
    LPCTSTR lpszProgID,  
    COleException* pError = NULL);
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 要建立的 `IDispatch` 連接物件類別識別碼。  
  
 `pError`  
 OLE 例外狀況物件的指標，會保留因建立而產生的狀態碼。  
  
 `lpszProgID`  
 Automation 物件之程式設計識別項的指標，例如 "Excel.Document.5"，針對此物件會建立分派物件。  
  
### <a name="return-value"></a>傳回值  
 非零成功，否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&4;](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]  
  
##  <a name="detachdispatch"></a>COleDispatchDriver::DetachDispatch  
 卸離目前`IDispatch`從此物件的連接。  
  
```  
LPDISPATCH DetachDispatch();
```  
  
### <a name="return-value"></a>傳回值  
 指向先前附加 OLE`IDispatch`物件。  
  
### <a name="remarks"></a>備註  
 `IDispatch`沒有釋出。  
  
 如需詳細資訊`LPDISPATCH`輸入資訊，請參閱[實作 IDispatch 介面](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&5;](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]  
  
##  <a name="getproperty"></a>COleDispatchDriver::GetProperty  
 取得所指定的物件屬性`dwDispID`。  
  
```  
void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>參數  
 `dwDispID`  
 識別要擷取的屬性。  
  
 `vtProp`  
 指定要擷取的屬性。 可能的值，請參閱 < 備註 > 一節[COleDispatchDriver::InvokeHelper](#invokehelper)。  
  
 `pvProp`  
 將會收到屬性值的變數的位址。 它必須符合所指定之類型`vtProp`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&6;](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]  
  
##  <a name="invokehelper"></a>COleDispatchDriver::InvokeHelper  
 在 `dwDispID`指定的內容中，呼叫物件方法或 `wFlags`所指定的屬性。  
  
```  
void AFX_CDECL InvokeHelper(
        DISPID dwDispID,  
        WORD wFlags,  
        VARTYPE vtRet,  
        void* pvRet,  
        const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>參數  
 `dwDispID`  
 指定所要叫用的屬性或方法。  
  
 `wFlags`  
 描述要呼叫 **IDispatch::Invoke**時之內容的旗標。 。 如需可能的值，請參閱`wFlags`中的參數[Excepinfo](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `vtRet`  
 指定傳回值的類型。 如需了解可能的值，請參閱＜備註＞一節。  
  
 `pvRet`  
 要接收屬性值或傳回值之變數的位址。 其必須符合 `vtRet`所指定的類型。  
  
 `pbParamInfo`  
 指定以 null終止，並尾隨在 `pbParamInfo`之後之參數類型的位元組的字串指標。  
  
 *...*  
 `pbParamInfo`中所指定之參數類型的變數清單。  
  
### <a name="remarks"></a>備註  
 `pbParamInfo` 參數會指定傳遞給方法或屬性的參數類型。 引數的變數清單會以 **...** 語法宣告代表。  
  
 `vtRet` 引數的可能值會從 `VARENUM` 列舉中取用。 可能的值如下：  
  
|符號|傳回類型|  
|------------|-----------------|  
|`VT_EMPTY`|`void`|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**日期**|  
|`VT_BSTR`|`BSTR`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  
  
 `pbParamInfo` 引數是以空格分隔的 **VTS_** 常數清單。 其中的一或多個值 (以空格分隔，而非逗號) 會指定函式的參數清單。 可能的值會與列出[EVENT_CUSTOM](event-maps.md#event_custom)巨集。  
  
 此函式會將參數轉換為 **VARIANTARG** 值，然後再叫用 [IDispatch::Invoke](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx) 方法。 若呼叫 `Invoke` 失敗，此函式會擲回例外狀況。 如果`SCODE`（狀態碼） 所傳回**Excepinfo**是`DISP_E_EXCEPTION`，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)物件; 否則會擲回[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)。  
  
 如需詳細資訊，請參閱[VARIANTARG](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)，[實作 IDispatch 介面](http://msdn.microsoft.com/library/windows/desktop/ms221037\(v=vs.85\).aspx)， [Excepinfo](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx)，和[COM 錯誤代碼結構](http://msdn.microsoft.com/library/windows/desktop/ms690088)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[COleDispatchDriver::CreateDispatch](#createdispatch)。  
  
##  <a name="m_bautorelease"></a>COleDispatchDriver::m_bAutoRelease  
 如果**TRUE**，來存取 COM 物件[m_lpDispatch](#m_lpdispatch)會自動釋放時[ReleaseDispatch](#releasedispatch)稱為或當這`COleDispatchDriver`物件被終結。  
  
```  
BOOL m_bAutoRelease;  
```  
  
### <a name="remarks"></a>備註  
 根據預設，`m_bAutoRelease`設為**TRUE**建構函式。  
  
 如需有關如何釋放 COM 物件的詳細資訊，請參閱[實作參考計數](http://msdn.microsoft.com/library/windows/desktop/ms693431)和[Iunknown](http://msdn.microsoft.com/library/windows/desktop/ms682317)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&9;](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]  
  
##  <a name="m_lpdispatch"></a>COleDispatchDriver::m_lpDispatch  
 將指標`IDispatch`介面附加至這個`COleDispatchDriver`。  
  
```  
LPDISPATCH m_lpDispatch;  
```  
  
### <a name="remarks"></a>備註  
 `m_lpDispatch`資料成員是類型的公用變數`LPDISPATCH`。  
  
 如需詳細資訊，請參閱[IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[COleDispatchDriver::AttachDispatch](#attachdispatch)。  
  
##  <a name="operator_eq"></a>COleDispatchDriver::operator =  
 複製到來源值`COleDispatchDriver`物件。  
  
```  
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>參數  
 `dispatchSrc`  
 指向現有的`COleDispatchDriver`物件。  
  
##  <a name="operator_lpdispatch"></a>COleDispatchDriver::operator LPDISPATCH  
 存取基礎`IDispatch`指標`COleDispatchDriver`物件。  
  
```  
operator LPDISPATCH();
```   
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&8;](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]  
  
##  <a name="releasedispatch"></a>COleDispatchDriver::ReleaseDispatch  
 版本`IDispatch`連線。 如需詳細資訊，請參閱[實作 IDispatch 介面](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)  
  
```  
void ReleaseDispatch();
```  
  
### <a name="remarks"></a>備註  
 如果此連線已設定自動發行，此函數會呼叫**IDispatch::Release**之前釋放介面。  
  
### <a name="example"></a>範例  
  請參閱範例[COleDispatchDriver::AttachDispatch](#attachdispatch)。  
  
##  <a name="setproperty"></a>COleDispatchDriver::SetProperty  
 設定 `dwDispID`指定的 OLE 物件屬性。  
  
```  
void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>參數  
 `dwDispID`  
 識別要設定的屬性。  
  
 `vtProp`  
 指定要設定的屬性類型。 可能的值，請參閱 < 備註 > 一節[COleDispatchDriver::InvokeHelper](#invokehelper)。  
  
 *...*  
 `vtProp`指定的類型單一參數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&7;](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CALCDRIV](../../visual-cpp-samples.md)   
 [MFC 範例 ACDUAL](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)

