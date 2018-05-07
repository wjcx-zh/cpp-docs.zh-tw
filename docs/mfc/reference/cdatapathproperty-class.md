---
title: CDataPathProperty 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2559b4917f16bb8ddc49b73ace8bda6e1a9bafc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty 類別
實作可以非同步載入的 OLE 控制項屬性。  
  
## <a name="syntax"></a>語法  
  
```  
class CDataPathProperty : public CAsyncMonikerFile  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|建構 `CDataPathProperty` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDataPathProperty::GetControl](#getcontrol)|擷取與相關聯的非同步 OLE 控制項`CDataPathProperty`物件。|  
|[CDataPathProperty::GetPath](#getpath)|擷取屬性的路徑名稱。|  
|[CDataPathProperty::Open](#open)|開始非同步的屬性相關聯的 ActiveX (OLE) 控制項載入。|  
|[CDataPathProperty::ResetData](#resetdata)|呼叫`CAsyncMonikerFile::OnDataAvailable`以通知容器控制項的屬性已變更。|  
|[CDataPathProperty::SetControl](#setcontrol)|設定與屬性相關聯的非同步 ActiveX (OLE) 控制項。|  
|[CDataPathProperty::SetPath](#setpath)|設定屬性的路徑名稱。|  
  
## <a name="remarks"></a>備註  
 非同步屬性會在同步初始之後載入。  
  
 類別`CDataPathProperty`衍生自**CAysncMonikerFile**。 若要實作 OLE 控制項非同步屬性，衍生自`CDataPathProperty`，並覆寫[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)。  
  
 如需如何在網際網路應用程式中使用非同步 moniker 以及 ActiveX 控制項的詳細資訊，請參閱下列文章：  
  
- [網際網路的第一個步驟： ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)  
  
- [非同步 Moniker 的網際網路第一個步驟：](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxctl.h  
  
##  <a name="cdatapathproperty"></a>  CDataPathProperty::CDataPathProperty  
 建構 `CDataPathProperty` 物件。  
  
```  
CDataPathProperty(COleControl* pControl = NULL);  
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pControl`  
 要與此相關聯的 OLE 控制項物件的指標`CDataPathProperty`物件。  
  
 `lpszPath`  
 路徑可能是絕對或相對，用來建立非同步 moniker 所參考之屬性的實際絕對位置。 `CDataPathProperty` 使用 Url，而不是檔名。 如果您想`CDataPathProperty`物件的檔案，請在前面加上`file://`的路徑。  
  
### <a name="remarks"></a>備註  
 `COleControl`指向的物件`pControl`正由**開啟**和擷取由衍生類別。 如果`pControl`是**NULL**，搭配使用的控制項**開啟**應該與設定`SetControl`。 如果`lpszPath`是**NULL**，您可以透過路徑中傳遞**開啟**，或將它與`SetPath`。  
  
##  <a name="getcontrol"></a>  CDataPathProperty::GetControl  
 呼叫此成員函式可擷取`COleControl`物件相關聯`CDataPathProperty`物件。  
  
```  
COleControl* GetControl();
```  
  
### <a name="return-value"></a>傳回值  
 OLE 控制項的指標相關聯的傳回`CDataPathProperty`物件。 **NULL**如果不是控制項相關聯。  
  
##  <a name="getpath"></a>  CDataPathProperty::GetPath  
 呼叫此成員函式，若要擷取的路徑，設定何時`CDataPathProperty`建構，或在指定物件**開啟**，或前一個呼叫中指定`SetPath`成員函式。  
  
```  
CString GetPath() const;  
```  
  
### <a name="return-value"></a>傳回值  
 屬性本身傳回的路徑名稱。 可以是空白，如果已指定沒有路徑。  
  
##  <a name="open"></a>  CDataPathProperty::Open  
 呼叫此成員函式，初始化相關聯的控制項非同步屬性載入。  
  
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
 檔案例外狀況的指標。 發生錯誤時，會設定為可能的原因。  
  
 `lpszPath`  
 路徑可能是絕對或相對，用來建立非同步 moniker 所參考之屬性的實際絕對位置。 `CDataPathProperty` 使用 Url，而不是檔名。 如果您想`CDataPathProperty`物件的檔案，請在前面加上`file://`的路徑。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 函式會嘗試取得`IBindHost`從控制項的介面。  
  
 然後再呼叫**開啟**沒有路徑，您必須設定屬性的路徑值。 這可以建構，或藉由呼叫物件時完成`SetPath`成員函式。  
  
 然後再呼叫**開啟**不受控制，ActiveX 控制項 （先前稱為 OLE 控制項） 可與物件相關聯。 這可以建構，或藉由呼叫物件時完成`SetControl`。  
  
 所有多載[CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open)您也可以從`CDataPathProperty`。  
  
##  <a name="resetdata"></a>  CDataPathProperty::ResetData  
 呼叫此函式可取得`CAsyncMonikerFile::OnDataAvailable`以通知容器控制項的屬性已變更，，和以非同步方式載入的所有資訊都都不再有用。  
  
```  
virtual void ResetData();
```  
  
### <a name="remarks"></a>備註  
 開啟應該重新啟動。 在衍生的類別可以覆寫這個函式供不同的預設值。  
  
##  <a name="setcontrol"></a>  CDataPathProperty::SetControl  
 呼叫此成員函式，使非同步 OLE 控制項與`CDataPathProperty`物件。  
  
```  
void SetControl(COleControl* pControl);
```  
  
### <a name="parameters"></a>參數  
 `pControl`  
 非同步的 OLE 控制項，要與屬性相關聯的指標。  
  
##  <a name="setpath"></a>  CDataPathProperty::SetPath  
 呼叫此成員函式可設定之屬性的路徑名稱。  
  
```  
void SetPath(LPCTSTR lpszPath);
```  
  
### <a name="parameters"></a>參數  
 `lpszPath`  
 路徑，但它可能是絕對或相對的以非同步方式載入的屬性。 `CDataPathProperty` 使用 Url，而不是檔名。 如果您想`CDataPathProperty`物件的檔案，請在前面加上`file://`的路徑。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例影像](../../visual-cpp-samples.md)   
 [CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)
