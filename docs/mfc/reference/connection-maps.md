---
title: "連接對應 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros.maps
dev_langs: C++
helpviewer_keywords: connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 018f2f6c1cd57dc500d4161b02ccb5880a9889fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="connection-maps"></a>連接對應
OLE 控制項都能將介面公開給其他應用程式。 這些介面只允許從容器的存取，至該控制項。 如果 OLE 控制項想要存取外部的其他 OLE 物件的介面，必須先建立的連接點。 此連接點可讓連出外部的分派對應，例如事件對應或通知函式的存取控制。  
  
 Microsoft Foundation 類別庫提供可支援的連接點的程式設計模型。 在此模型中，「 連接對應 」 用於指定的 OLE 控制項的連接點或介面。 連接對應包含一個巨集，每個連接點。 如需有關連接對應的詳細資訊，請參閱[CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md)類別。  
  
 一般而言，控制項將支援兩個連接點： 其中一個事件，另一個屬性通知。 這些由實作`COleControl`基底類別，且需要寫入器會控制任何其他工作。 您想要實作您類別中的任何其他連接點必須手動加入。 若要支援連接對應和點，MFC 提供下列巨集：  
  
### <a name="connection-map-declaration-and-demarcation"></a>連接對應宣告和區分  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_PART](#begin_connection_part)|宣告內嵌的類別，實作 （必須用於類別宣告中） 的其他連接點。|  
|[END_CONNECTION_PART](#end_connection_part)|宣告的結尾 （必須用於類別宣告中） 的連接點。|  
|[CONNECTION_IID](#connection_iid)|指定控制項的連接點的介面 ID。|  
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|宣告連接對應將用於 （必須用於類別宣告中） 的類別。|  
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|開始連接對應 （必須用於類別實作中） 的定義。|  
|[END_CONNECTION_MAP](#end_connection_map)|結束連接對應 （必須用於類別實作中） 的定義。|  
|[CONNECTION_PART](#connection_part)|指定控制項的連線對應的連接點。|  
  
 下列函數協助建立和使用的連接點的連線中斷連線接收：  
  
### <a name="initializationtermination-of-connection-points"></a>初始化/終止的連接點  
  
|||  
|-|-|  
|[AfxConnectionAdvise](#afxconnectionadvise)|建立來源與接收器之間的連接。|  
|[AfxConnectionUnadvise](#afxconnectionunadvise)|在來源與接收器之間的連接會中斷。|  
  
##  <a name="begin_connection_part"></a>BEGIN_CONNECTION_PART  
 使用`BEGIN_CONNECTION_PART`巨集，以開始事件和屬性通知連接點以外的其他連接點的定義。  
  
```   
BEGIN_CONNECTION_PART(theClass, localClass)   
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 指定的連接點，這樣的控制項類別名稱。  
  
 *localClass*  
 指定實作連接點之區域類別的名稱。  
  
### <a name="remarks"></a>備註  
 在定義類別的成員函式宣告 (.h) 檔案中，啟動 連接點`BEGIN_CONNECTION_PART`巨集，然後新增`CONNECTION_IID`巨集和您想要實作，並完成 連接點對應任何其他成員函式與`END_CONNECTION_PART`巨集。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="end_connection_part"></a>END_CONNECTION_PART  
 結束連接點的宣告。  
  
```   
END_CONNECTION_PART(localClass)   
```  
  
### <a name="parameters"></a>參數  
 *localClass*  
 指定實作連接點之區域類別的名稱。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="connection_iid"></a>CONNECTION_IID  
 在 `BEGIN_CONNECTION_PART` 和 `END_CONNECTION_PART` 巨集間使用，為 OLE Automation 控制項支授的連接點定義介面 ID。  
  
```   
CONNECTION_IID(iid)   
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 連接點所呼叫介面的介面 ID。  
  
### <a name="remarks"></a>備註  
 `iid` 引數是用於識別連接點將在其連接的接收器上呼叫之介面的介面 ID。 例如:   
  
 [!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]  
  
 指定呼叫 `ISinkInterface` 介面的連接點。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="declare_connection_map"></a>DECLARE_CONNECTION_MAP  
 程式中的每個 `COleControl` 衍生類別都可以提供一個連接對應，用於指定您的控制項所支援的其他連接點。  
  
```   
DECLARE_CONNECTION_MAP() 
```  
  
### <a name="remarks"></a>備註  
 如果控制項支援額外的連接點，請在類別宣告的結尾處使用 `DECLARE_CONNECTION_MAP` 巨集。 然後，在定義類別成員函式的 .cpp 檔案中使用 `BEGIN_CONNECTION_MAP` 巨集、針對每個控制項的連接點使用 `CONNECTION_PART` 巨集，以及使用 `END_CONNECTION_MAP` 巨集來宣告連接對應的結尾。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="begin_connection_map"></a>BEGIN_CONNECTION_MAP  
 程式中每個 `COleControl` 衍生類別可以提供連接對應，以指定控制項支援的連接點。  
  
```   
BEGIN_CONNECTION_MAP(theClass, theBase)   
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 指定連接對應之控制項類別的名稱。  
  
 *theBase*  
 指定 `theClass` 基底類別的名稱。  
  
### <a name="remarks"></a>備註  
 在實作 (。定義您的類別成員函式的 CPP) 檔案啟動連接對應與`BEGIN_CONNECTION_MAP`巨集，然後將巨集項目加入您的連線點使用的每個[CONNECTION_PART](#connection_part)巨集。 最後，完成連接對應與[END_CONNECTION_MAP](#end_connection_map)巨集。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="end_connection_map"></a>END_CONNECTION_MAP  
 結束連接對應的定義。  
  
```   
END_CONNECTION_MAP()  
```  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="connection_part"></a>CONNECTION_PART  
 OLE 控制項的連接點會對應至特定的介面識別碼。  
  
```   
CONNECTION_PART(theClass, iid, localClass)   
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 指定的連接點，這樣的控制項類別名稱。  
  
 `iid`  
 連接點所呼叫介面的介面 ID。  
  
 *localClass*  
 指定實作連接點之區域類別的名稱。  
  
### <a name="remarks"></a>備註  
 例如:   
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]  
  
 實作連接對應，與連接點，會呼叫`IID_ISinkInterface`介面。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdisp.h  
  
##  <a name="afxconnectionadvise"></a>AfxConnectionAdvise  
 呼叫此函式可指定來源之間建立連線`pUnkSrc`，與所指定的接收`pUnkSink`。  
  
```   
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD FAR* pdwCookie);
```  
  
### <a name="parameters"></a>參數  
 `pUnkSrc`  
 呼叫介面的物件指標。  
  
 `pUnkSink`  
 實作介面的物件指標。  
  
 `iid`  
 連接的介面識別碼。  
  
 `bRefCount`  
 **TRUE**表示建立的連接應該會使參考計數的`pUnkSink`遞增。 **FALSE**指出應該不會遞增參考計數。  
  
 `pdwCookie`  
 指標`DWORD`傳回連接識別碼的位置。 此值應傳遞做為`dwCookie`參數`AfxConnectionUnadvise`時中斷連線的連線。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已建立連線;否則便是 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afxctl.h 

##  <a name="afxconnectionunadvise"></a>AfxConnectionUnadvise  
 呼叫此函式來中斷連線之間指定的來源`pUnkSrc`，與所指定的接收`pUnkSink`。  
  
```   
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD dwCookie); 
```  
  
### <a name="parameters"></a>參數  
 `pUnkSrc`  
 呼叫介面的物件指標。  
  
 `pUnkSink`  
 實作介面的物件指標。  
  
 `iid`  
 連接點介面的介面識別碼。  
  
 `bRefCount`  
 **TRUE**表示中斷連線的連線應該會使參考計數的`pUnkSink`會減少。 **FALSE**表示不應該遞減參考計數。  
  
 `dwCookie`  
 所傳回的連接識別碼`AfxConnectionAdvise`。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果連線已中斷連線。否則便是 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** afxctl.h 

## <a name="see-also"></a>請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)
