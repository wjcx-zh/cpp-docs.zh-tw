---
title: "CCachedDataPathProperty 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
dev_langs: C++
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2fb62a905d092a347103ea98fcd323e3778ed458
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccacheddatapathproperty-class"></a>CCachedDataPathProperty 類別
實作非同步傳輸且在記憶體檔案中快取的 OLE 控制項屬性。  
  
## <a name="syntax"></a>語法  
  
```  
class CCachedDataPathProperty : public CDataPathProperty  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|建構 `CCachedDataPathProperty` 物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile`物件的快取資料。|  
  
## <a name="remarks"></a>備註  
 記憶體檔案儲存在 RAM 中，而不是磁碟上，並可用於快速暫時的傳輸。  
  
 連同**CAysncMonikerFile**和`CDataPathProperty`，`CCachedDataPathProperty`提供使用非同步 moniker 中 OLE 控制項的功能。 與`CCachedDataPathProperty`物件，您便能夠 URL 或檔案的來源，以非同步方式傳送資料，並將它儲存在記憶體檔案，透過`m_Cache`公用變數。 所有資料都會儲存在記憶體檔案中，而且不需要覆寫[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)除非您想要監看的通知，並回應。 例如，如果您要傳送的大型。GIF 檔案，而且想来通知您的控制項，詳細資料已送達，和它應該重繪其本身，覆寫`OnDataAvailable`進行通知。  
  
 類別`CCachedDataPathProperty`衍生自`CDataPathProperty`。  
  
 如需如何在網際網路應用程式中使用非同步 moniker 以及 ActiveX 控制項的詳細資訊，請參閱下列主題：  
  
- [網際網路的第一個步驟： ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)  
  
- [非同步 Moniker 的網際網路第一個步驟：](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)  
  
 `CCachedDataPathProperty`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxctl.h  
  
##  <a name="ccacheddatapathproperty"></a>CCachedDataPathProperty::CCachedDataPathProperty  
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
 路徑可能是絕對或相對，用來建立非同步 moniker 所參考之屬性的實際絕對位置。 `CCachedDataPathProperty`使用 Url，而不是檔名。 如果您想`CCachedDataPathProperty`物件的檔案，前面加上 file:// 路徑。  
  
### <a name="remarks"></a>備註  
 `COleControl`指向的物件`pControl`正由[開啟](../../mfc/reference/cdatapathproperty-class.md#open)和擷取由衍生類別。 如果`pControl`是**NULL**，搭配使用的控制項**開啟**應該與設定[SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol)。 如果`lpszPath`是**NULL**，您可以透過路徑中傳遞**開啟**，或將它與[SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath)。  
  
##  <a name="m_cache"></a>CCachedDataPathProperty::m_Cache  
 包含類別檔案名稱的記憶體快取到其中的資料。  
  
```  
CMemFile m_Cache;  
```  
  
### <a name="remarks"></a>備註  
 記憶體檔案會儲存在 RAM 中，而不是磁碟上。  
  
## <a name="see-also"></a>請參閱  
 [CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)
