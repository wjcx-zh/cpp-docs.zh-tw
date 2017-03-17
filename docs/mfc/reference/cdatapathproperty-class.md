---
title: "CDataPathProperty 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], asynchronous
- OLE controls [C++], asynchronous
- CDataPathProperty class
- asynchronous controls [C++]
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
caps.latest.revision: 24
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
ms.openlocfilehash: d767cf950d8b86959aadc2fd4d77401134a6dc75
ms.lasthandoff: 02/24/2017

---
# <a name="cdatapathproperty-class"></a>CDataPathProperty 類別
實作可以非同步載入的 OLE 控制項屬性。  
  
## <a name="syntax"></a>語法  
  
```  
class CDataPathProperty : public CAsyncMonikerFile  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|建構 `CDataPathProperty` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDataPathProperty::GetControl](#getcontrol)|擷取相關聯的非同步 OLE 控制項`CDataPathProperty`物件。|  
|[CDataPathProperty::GetPath](#getpath)|擷取屬性的路徑名稱。|  
|[CDataPathProperty::Open](#open)|初始載入相關聯的 ActiveX (OLE) 控制項的非同步屬性。|  
|[CDataPathProperty::ResetData](#resetdata)|呼叫`CAsyncMonikerFile::OnDataAvailable`以通知容器控制項的屬性已變更。|  
|[CDataPathProperty::SetControl](#setcontrol)|設定與屬性相關聯的非同步 ActiveX (OLE) 控制。|  
|[CDataPathProperty::SetPath](#setpath)|設定屬性的路徑名稱。|  
  
## <a name="remarks"></a>備註  
 非同步屬性會在同步初始之後載入。  
  
 類別`CDataPathProperty`衍生自**CAysncMonikerFile**。 OLE 控制項實作非同步屬性，衍生自`CDataPathProperty`，並覆寫[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)。  
  
 如需如何在 網際網路應用程式中使用非同步 moniker 和 ActiveX 控制項的詳細資訊，請參閱下列文章︰  
  
- [網際網路的第一個步驟︰ ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)  
  
- [非同步 Moniker 的網際網路第一個步驟︰](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxctl.h  
  
##  <a name="cdatapathproperty"></a>CDataPathProperty::CDataPathProperty  
 建構 `CDataPathProperty` 物件。  
  
```  
CDataPathProperty(COleControl* pControl = NULL);  
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pControl`  
 要與此相關聯的 OLE 控制項物件的指標`CDataPathProperty`物件。  
  
 `lpszPath`  
 路徑可以是絕對或相對，用來建立參考之屬性的實際絕對位置，非同步 moniker。 `CDataPathProperty`會使用 Url，不是檔名。 如果您想`CDataPathProperty`物件的檔案，在前面加上`file://`的路徑。  
  
### <a name="remarks"></a>備註  
 `COleControl`指向的物件`pControl`由**開啟**，並且擷取衍生的類別。 如果`pControl`是**NULL**，搭配使用的控制項**開啟**應該與設定`SetControl`。 如果`lpszPath`是**NULL**，您可以透過路徑中傳遞**開啟**，或將它與`SetPath`。  
  
##  <a name="getcontrol"></a>CDataPathProperty::GetControl  
 呼叫此成員函式擷取`COleControl`物件相關聯`CDataPathProperty`物件。  
  
```  
COleControl* GetControl();
```  
  
### <a name="return-value"></a>傳回值  
 傳回與關聯的 OLE 控制項的指標`CDataPathProperty`物件。 **NULL**如果不是控制項相關聯。  
  
##  <a name="getpath"></a>CDataPathProperty::GetPath  
 呼叫此成員函式，擷取路徑，請設定當`CDataPathProperty`建構，或在指定物件**開啟**，或在前一次呼叫中指定`SetPath`成員函式。  
  
```  
CString GetPath() const;  
```  
  
### <a name="return-value"></a>傳回值  
 屬性本身傳回的路徑名稱。 可以是空白，如果未不指定任何路徑。  
  
##  <a name="open"></a>CDataPathProperty::Open  
 呼叫此成員函式，以起始非同步屬性相關聯控制項的載入。  
  
```  
virtual BOOL Open(
    COleControl* pControl,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    COleControl* pControl,
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    CFileException* pError = NULL);  
  
virtual BOOL Open(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pControl`  
 要與此相關聯的 OLE 控制項物件的指標`CDataPathProperty`物件。  
  
 `pError`  
 檔案例外狀況的指標。 發生錯誤時，將可能的原因。  
  
 `lpszPath`  
 路徑可以是絕對或相對，用來建立參考之屬性的實際絕對位置，非同步 moniker。 `CDataPathProperty`會使用 Url，不是檔名。 如果您想`CDataPathProperty`物件的檔案，在前面加上`file://`的路徑。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 函式會嘗試取得`IBindHost`從控制項的介面。  
  
 然後再呼叫**開啟**不包含路徑，您必須設定屬性的路徑值。 這可以建構，或藉由呼叫物件時`SetPath`成員函式。  
  
 然後再呼叫**開啟**不受控制，ActiveX 控制項 （先前稱為 OLE 控制項） 可以是與物件相關聯。 這可以建構，或藉由呼叫物件時`SetControl`。  
  
 所有多載[CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open)也都由`CDataPathProperty`。  
  
##  <a name="resetdata"></a>CDataPathProperty::ResetData  
 呼叫此函式可取得`CAsyncMonikerFile::OnDataAvailable`以通知容器，控制項屬性已變更，並以非同步方式載入的所有資訊都都不再有用。  
  
```  
virtual void ResetData();
```  
  
### <a name="remarks"></a>備註  
 開啟應該重新啟動。 在衍生的類別可以覆寫這個函式供不同的預設值。  
  
##  <a name="setcontrol"></a>CDataPathProperty::SetControl  
 呼叫此成員函式，將以非同步的 OLE 控制項相關聯`CDataPathProperty`物件。  
  
```  
void SetControl(COleControl* pControl);
```  
  
### <a name="parameters"></a>參數  
 `pControl`  
 非同步的 OLE 控制項，與屬性相關聯的指標。  
  
##  <a name="setpath"></a>CDataPathProperty::SetPath  
 呼叫此成員函式設定屬性的路徑名稱。  
  
```  
void SetPath(LPCTSTR lpszPath);
```  
  
### <a name="parameters"></a>參數  
 `lpszPath`  
 路徑，可能是絕對或相對的以非同步方式載入的屬性。 `CDataPathProperty`會使用 Url，不是檔名。 如果您想`CDataPathProperty`物件的檔案，在前面加上`file://`的路徑。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例的影像](../../visual-cpp-samples.md)   
 [CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)

