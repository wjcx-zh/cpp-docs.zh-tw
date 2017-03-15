---
title: "CCachedDataPathProperty 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCachedDataPathProperty
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], asynchronous
- CCachedDataPathProperty class
- OLE controls [C++], asynchronous
- asynchronous controls [C++]
- memory files [C++]
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
caps.latest.revision: 22
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
ms.openlocfilehash: 6e3f54e6429456be24cbe18471abd1705bbe0034
ms.lasthandoff: 02/24/2017

---
# <a name="ccacheddatapathproperty-class"></a>CCachedDataPathProperty 類別
實作非同步傳輸且在記憶體檔案中快取的 OLE 控制項屬性。  
  
## <a name="syntax"></a>語法  
  
```  
class CCachedDataPathProperty : public CDataPathProperty  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|建構 `CCachedDataPathProperty` 物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile`物件，其中快取資料。|  
  
## <a name="remarks"></a>備註  
 記憶體檔案儲存在 RAM 中，而不是在磁碟上，並可用於快速暫時的傳輸。  
  
 連同**CAysncMonikerFile**和`CDataPathProperty`， `CCachedDataPathProperty` OLE 控制項中的非同步 moniker 的使用提供的功能。 使用`CCachedDataPathProperty`物件時，您就可以從 URL 或檔案的來源以非同步方式傳送資料，並將它儲存在記憶體檔案透過`m_Cache`公用變數。 所有資料都儲存在記憶體檔案中，並不需要覆寫[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)除非您想要監看通知並回應。 例如，如果您傳輸大量。GIF 檔案，且想来通知您的控制項，詳細資料已送達，和它應該重繪其本身，覆寫`OnDataAvailable`進行通知。  
  
 類別`CCachedDataPathProperty`衍生自`CDataPathProperty`。  
  
 如需如何在 網際網路應用程式中使用非同步 moniker 和 ActiveX 控制項的詳細資訊，請參閱下列主題︰  
  
- [網際網路的第一個步驟︰ ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)  
  
- [非同步 Moniker 的網際網路第一個步驟︰](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)  
  
 `CCachedDataPathProperty`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxctl.h  
  
##  <a name="a-nameccacheddatapathpropertya--ccacheddatapathpropertyccacheddatapathproperty"></a><a name="ccacheddatapathproperty"></a>CCachedDataPathProperty::CCachedDataPathProperty  
 建構 `CCachedDataPathProperty` 物件。  
  
```  
CCachedDataPathProperty(COleControl* pControl = NULL);

 
CCachedDataPathProperty(
    LPCTSTR lpszPath,  
    COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pControl`  
 要與此相關聯的 ActiveX 控制項物件的指標`CCachedDataPathProperty`物件。  
  
 `lpszPath`  
 路徑可以是絕對或相對，用來建立參考之屬性的實際絕對位置，非同步 moniker。 `CCachedDataPathProperty`會使用 Url，不是檔名。 如果您想`CCachedDataPathProperty`物件的檔案，在前面加上路徑 file://。  
  
### <a name="remarks"></a>備註  
 `COleControl`指向的物件`pControl`由[開啟](../../mfc/reference/cdatapathproperty-class.md#open)，並且擷取衍生的類別。 如果`pControl`是**NULL**，搭配使用的控制項**開啟**應該與設定[SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol)。 如果`lpszPath`是**NULL**，您可以透過路徑中傳遞**開啟**，或將它與[SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath)。  
  
##  <a name="a-namemcachea--ccacheddatapathpropertymcache"></a><a name="m_cache"></a>CCachedDataPathProperty::m_Cache  
 包含資料快取到記憶體檔案類別的名稱。  
  
```  
CMemFile m_Cache;  
```  
  
### <a name="remarks"></a>備註  
 記憶體檔案會儲存在 RAM 中，而不是在磁碟上。  
  
## <a name="see-also"></a>另請參閱  
 [CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)

