---
title: "COM 對應巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
caps.latest.revision: 16
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 79658b6ac22719af7172c9d2848675faf2a23a0c
ms.lasthandoff: 02/24/2017

---
# <a name="com-map-macros"></a>COM 對應巨集
這些巨集定義 COM 介面對應。  
  
|||  
|-|-|  
|[BEGIN_COM_MAP](#begin_com_map)|標記 COM 介面對應項目的開頭。|  
|[COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)|介面進入 COM 介面對應。|  
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|使用這個巨集來區分兩個分支的繼承。|  
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|使用這個巨集輸入到 COM 對應的介面，並指定其 IID。|  
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|相同[COM_INTERFACE_ENTRY2](#com_interface_entry2)，但您可以指定不同的 IID。|  
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|當此介面由`iid`查詢時，`COM_INTERFACE_ENTRY_AGGREGATE`轉送給`punk`。|  
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，差別只在於轉送查詢來查詢任何 IID 產生`punk`。|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非`punk`是**NULL**，它會自動建立所描述的彙總`clsid`。|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|相同[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)，差別只在於查詢的任何 IID 導致轉送查詢`punk`，而且如果`punk`是**NULL**就會自動建立所描述的彙總`clsid`。|  
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|讓程式呼叫[DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297)時指定的介面中查詢。|  
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|將每個執行個體的指定介面的資料儲存。|  
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|會公開您 tear-off 介面。|  
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|處理 COM 對應的基底類別處理到達此 COM 對應中的項目時。|  
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|連結到 ATL 的一般機制`QueryInterface`邏輯。|  
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|相同[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)，差別只在於查詢的任何 IID 導致呼叫`func`。|  
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|傳回**E_NOINTERFACE**並終止 COM 對應處理時，查詢指定的介面。|  
|[END_COM_MAP](#end_com_map)|COM 介面對應項目結束標記。|  

## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
   
##  <a name="a-namebegincommapa--begincommap"></a><a name="begin_com_map"></a>BEGIN_COM_MAP  
 COM 對應是透過用戶端物件上的介面公開 （expose） 的機制`QueryInterface`。  
  
```
BEGIN_COM_MAP(x)
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]您要公開的介面的類別物件的名稱。  
  
### <a name="remarks"></a>備註  
 [CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) COM 對應中只會傳回介面指標。 啟動您的介面對應與`BEGIN_COM_MAP`巨集，為您的介面，以及每個新增項目[COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/c5363b8b-a1a2-471e-ad3a-d472f6c356c5)巨集或其中一個變化，並完成的對應[END_COM_MAP](#end_com_map)巨集。  

  
### <a name="example"></a>範例  
 Atl[呼叫器](../../visual-cpp-samples.md)範例︰  
  
 [!code-cpp[NVC_ATL_COM&#1;](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  
##  <a name="a-namecominterfaceentrymacrosa--cominterfaceentry-macros"></a><a name="com_interface_entry_macros"></a>COM_INTERFACE_ENTRY 巨集  
 這些巨集的物件將介面輸入到其 COM 對應，讓他們可以存取`QueryInterface`。 COM 對應中的項目順序是訂單介面會檢查相符**IID**期間`QueryInterface`。  
  
##  <a name="a-namecominterfaceentry2x2a--cominterfaceentry2"></a><a name="com_interface_entry2_x2"></a>COM_INTERFACE_ENTRY2  
 使用這個巨集來區分兩個分支的繼承。  
  
```
COM_INTERFACE_ENTRY2(x, x2)
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]您要從您的物件公開的介面名稱。  
  
 `x2`  
 [in]從中繼承分支的名稱*x*公開。  
  
### <a name="remarks"></a>備註  
 例如，如果衍生類別物件，這兩個雙介面，您將公開`IDispatch`使用`COM_INTERFACE_ENTRY2`因為`IDispatch`可以取自其中一種介面。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&118;](../../atl/codesnippet/cpp/com-map-macros_2.h)]  
  
##  <a name="a-namecominterfaceentryiida--cominterfaceentryiid"></a><a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID  
 使用這個巨集輸入到 COM 對應的介面，並指定其 IID。  
  
```
COM_INTERFACE_ENTRY_IID(iid, x)
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]公開的介面的 GUID。  
  
 *x*  
 [in]類別的 vtable 即將公開為所識別的介面名稱`iid`。  
  
### <a name="remarks"></a>備註  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&117;](../../atl/codesnippet/cpp/com-map-macros_3.h)]  
  
##  <a name="a-namecominterfaceentry2iida--cominterfaceentry2iid"></a><a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID  
 相同[COM_INTERFACE_ENTRY2](#com_interface_entry2)，但您可以指定不同的 IID。  
  
```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```   
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]您指定介面的 GUID。  
  
 *x*  
 [in]類別物件直接衍生自介面的名稱。  
  
 `x2`  
 [in]第二個類別物件直接衍生自介面的名稱。  
  
### <a name="remarks"></a>備註  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
##  <a name="a-namecominterfaceentry2a--cominterfaceentry2"></a><a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2  
 使用這個巨集來區分兩個分支的繼承。  
  
```
COM_INTERFACE_ENTRY2(x, x2)
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]您要從您的物件公開的介面名稱。  
  
 `x2`  
 [in]從中繼承分支的名稱*x*公開。  
  
### <a name="remarks"></a>備註  
 例如，如果衍生類別物件，這兩個雙介面，您將公開`IDispatch`使用`COM_INTERFACE_ENTRY2`因為`IDispatch`可以取自其中一種介面。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&118;](../../atl/codesnippet/cpp/com-map-macros_2.h)]  
  
##  <a name="a-namecominterfaceentryaggregate2a--cominterfaceentryaggregate"></a><a name="com_interface_entry_aggregate2"></a>COM_INTERFACE_ENTRY_AGGREGATE  
 當此介面由`iid`查詢時，`COM_INTERFACE_ENTRY_AGGREGATE`轉送給`punk`。  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]查詢介面的 GUID。  
  
 `punk`  
 [in]名稱**IUnknown**指標。  
  
### <a name="remarks"></a>備註  
 `punk`參數會假設為指向內部未知的彙總或**NULL**，在此情況下會忽略此項目。 一般而言，您會**CoCreate**中的彙總`FinalConstruct`。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&112;](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="a-namecominterfaceentryaggregateblinda--cominterfaceentryaggregateblind"></a><a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND  
 相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，差別只在於轉送查詢來查詢任何 IID 產生`punk`。  
  
```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```  
  
### <a name="parameters"></a>參數  
 `punk`  
 [in]名稱**IUnknown**指標。  
  
### <a name="remarks"></a>備註  
 如果介面查詢將會失敗，會繼續處理 COM 對應。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&113;](../../atl/codesnippet/cpp/com-map-macros_5.h)]  
  
##  <a name="a-namecominterfaceentryaggregate3a--cominterfaceentryaggregate"></a><a name="com_interface_entry_aggregate3"></a>COM_INTERFACE_ENTRY_AGGREGATE  
 當此介面由`iid`查詢時，`COM_INTERFACE_ENTRY_AGGREGATE`轉送給`punk`。  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]查詢介面的 GUID。  
  
 `punk`  
 [in]名稱**IUnknown**指標。  
  
### <a name="remarks"></a>備註  
 `punk`參數會假設為指向內部未知的彙總或**NULL**，在此情況下會忽略此項目。 一般而言，您會**CoCreate**中的彙總`FinalConstruct`。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&112;](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="a-namecominterfaceentryautoaggregatea--cominterfaceentryautoaggregate"></a><a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE  
 相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非`punk`是**NULL**，它會自動建立所描述的彙總`clsid`。  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```   
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]查詢介面的 GUID。  
  
 `punk`  
 [in]名稱**IUnknown**指標。 必須是包含 COM 對應之類別的成員。  
  
 `clsid`  
 [in]如果建立的彙總的識別項`punk`是**NULL**。  
  
### <a name="remarks"></a>備註  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&114;](../../atl/codesnippet/cpp/com-map-macros_6.h)]  
  
##  <a name="a-namecominterfaceentryaggregatea--cominterfaceentryaggregate"></a><a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE  
 當此介面由`iid`查詢時，`COM_INTERFACE_ENTRY_AGGREGATE`轉送給`punk`。  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]查詢介面的 GUID。  
  
 `punk`  
 [in]名稱**IUnknown**指標。  
  
### <a name="remarks"></a>備註  
 `punk`參數會假設為指向內部未知的彙總或**NULL**，在此情況下會忽略此項目。 一般而言，您會**CoCreate**中的彙總`FinalConstruct`。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&112;](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="a-namecominterfaceentryautoaggregateblinda--cominterfaceentryautoaggregateblind"></a><a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND  
 相同[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)，差別只在於查詢的任何 IID 導致轉送查詢`punk`，而且如果`punk`是**NULL**就會自動建立所描述的彙總`clsid`。  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```  
  
### <a name="parameters"></a>參數  
 `punk`  
 [in]名稱**IUnknown**指標。 必須是包含 COM 對應之類別的成員。  
  
 `clsid`  
 [in]如果建立的彙總的識別項`punk`是**NULL**。  
  
### <a name="remarks"></a>備註  
 如果介面查詢將會失敗，會繼續處理 COM 對應。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&115;](../../atl/codesnippet/cpp/com-map-macros_7.h)]  
  
##  <a name="a-namecominterfaceentryautoaggregate2a--cominterfaceentryautoaggregate"></a><a name="com_interface_entry_autoaggregate2"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE  
 相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非`punk`是**NULL**，它會自動建立所描述的彙總`clsid`。  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```   
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]查詢介面的 GUID。  
  
 `punk`  
 [in]名稱**IUnknown**指標。 必須是包含 COM 對應之類別的成員。  
  
 `clsid`  
 [in]如果建立的彙總的識別項`punk`是**NULL**。  
  
### <a name="remarks"></a>備註  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&114;](../../atl/codesnippet/cpp/com-map-macros_6.h)]  
  
##  <a name="a-namecominterfaceentrybreaka--cominterfaceentrybreak"></a><a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK  
 讓程式呼叫[DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297)時指定的介面中查詢。  
  
```
COM_INTERFACE_ENTRY_BREAK(x)
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]用來建構的介面識別項的文字。  
  
### <a name="remarks"></a>備註  
 介面的 IID，就會建構，加上*x*到`IID_`。 例如，如果*x*是`IPersistStorage`，將 IID `IID_IPersistStorage`。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
##  <a name="a-namecominterfaceentrycachedtearoffa--cominterfaceentrycachedtearoff"></a><a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF  
 將每個執行個體的指定介面的資料儲存。  
  
```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```   
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]撕下介面的 GUID。  
  
 *x*  
 [in]實作介面的類別名稱。  
  
 `punk`  
 [in]名稱**IUnknown**指標。 必須是包含 COM 對應之類別的成員。 應該先初始化才能**NULL**類別物件的建構函式中。  
  
### <a name="remarks"></a>備註  
 如果未使用的介面，這會減少整體的執行個體大小的物件。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM&#54;](../../atl/codesnippet/cpp/com-map-macros_8.h)]  
  
##  <a name="a-namecominterfaceentrytearoffa--cominterfaceentrytearoff"></a><a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF  
 會公開您 tear-off 介面。  
  
```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]撕下介面的 GUID。  
  
 *x*  
 [in]實作介面的類別名稱。  
  
### <a name="remarks"></a>備註  
 撕下介面的實作方式會具現化每次它所代表之介面的另一個物件查詢。 一般而言，您建置您的介面為撕如果很少使用的介面，因為這會在主要物件的每個執行個體中儲存的 vtable 指標。 撕下會刪除其參考計數變成零時。 撕下實作的類別必須衍生自`CComTearOffObjectBase`而且有它自己的 COM 對應。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM&#1;](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  
##  <a name="a-namecominterfaceentrychaina--cominterfaceentrychain"></a><a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN  
 處理 COM 對應的基底類別處理到達此 COM 對應中的項目時。  
  
```
COM_INTERFACE_ENTRY_CHAIN(classname)
```  
  
### <a name="parameters"></a>參數  
 *類別名稱*  
 [in]目前物件的基底類別。  
  
### <a name="remarks"></a>備註  
 例如，在下列程式碼︰  
  
 [!code-cpp[NVC_ATL_Windowing&116;](../../atl/codesnippet/cpp/com-map-macros_9.h)]  
  
 請注意 COM 對應中的第一個項目必須包含 COM 對應的物件上的介面。 因此，您無法啟動您的 COM 對應項目與`COM_INTERFACE_ENTRY_CHAIN`，而導致不同的物件，來搜尋的點的 COM 對應其中**COM_INTERFACE_ENTRY_CHAIN (**`COtherObject`**)**會出現在物件的 COM 對應。 如果您想要搜尋的另一個物件的 COM 對應，首先，新增介面項目**IUnknown**至 COM 對應，然後鏈結的其他物件的 COM 對應。 例如:   
  
 [!code-cpp[NVC_ATL_Windowing #&111;](../../atl/codesnippet/cpp/com-map-macros_10.h)]  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
##  <a name="a-namecominterfaceentryfunc2a--cominterfaceentryfunc"></a><a name="com_interface_entry_func2"></a>COM_INTERFACE_ENTRY_FUNC  
 連結到 ATL 的一般機制`QueryInterface`邏輯。  
  
```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```   
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]公開的介面的 GUID。  
  
 `dw`  
 [in]為參數傳遞到`func`。  
  
 `func`  
 [in]函式指標，它會傳回`iid`。  
  
### <a name="remarks"></a>備註  
 如果*iid*符合的查詢，介面則所指定的函數 IID`func`呼叫。 函式的宣告應該是︰  
  
 `HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`  
  
 您的函式呼叫時，`pv`指向類別的物件。 `riid`參數指的是，正在查詢的介面`ppv`是函式應該存放到介面指標的位置的指標和`dw`是您指定的項目中的參數。 函式應該設定\*`ppv`至**NULL** ，並傳回**E_NOINTERFACE**或**S_FALSE**如果選擇不是要傳回的介面。 使用**E_NOINTERFACE**，COM 對應處理會終止。 使用**S_FALSE**，COM 對應處理會繼續，即使未傳回任何介面指標。 如果函數傳回的介面指標，它應該傳回`S_OK`。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
##  <a name="a-namecominterfaceentryfuncblinda--cominterfaceentryfuncblind"></a><a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND  
 相同[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)，差別只在於查詢的任何 IID 導致呼叫`func`。  
  
```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```  
  
### <a name="parameters"></a>參數  
 `dw`  
 [in]為參數傳遞到`func`。  
  
 `func`  
 [in]取得處理 COM 對應中的此項目時呼叫的函式。  
  
### <a name="remarks"></a>備註  
 處理 COM 對應上繼續時，會發生任何錯誤。 如果函數傳回的介面指標，它應該傳回`S_OK`。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
##  <a name="a-namecominterfaceentryfunca--cominterfaceentryfunc"></a><a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC  
 連結到 ATL 的一般機制`QueryInterface`邏輯。  
  
```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```   
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]公開的介面的 GUID。  
  
 `dw`  
 [in]為參數傳遞到`func`。  
  
 `func`  
 [in]函式指標，它會傳回`iid`。  
  
### <a name="remarks"></a>備註  
 如果*iid*符合的查詢，介面則所指定的函數 IID`func`呼叫。 函式的宣告應該是︰  
  
 `HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`  
  
 您的函式呼叫時，`pv`指向類別的物件。 `riid`參數指的是，正在查詢的介面`ppv`是函式應該存放到介面指標的位置的指標和`dw`是您指定的項目中的參數。 函式應該設定\*`ppv`至**NULL** ，並傳回**E_NOINTERFACE**或**S_FALSE**如果選擇不是要傳回的介面。 使用**E_NOINTERFACE**，COM 對應處理會終止。 使用**S_FALSE**，COM 對應處理會繼續，即使未傳回任何介面指標。 如果函數傳回的介面指標，它應該傳回`S_OK`。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
##  <a name="a-namecominterfaceentrynointerfacea--cominterfaceentrynointerface"></a><a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE  
 傳回**E_NOINTERFACE**並終止 COM 對應處理時，查詢指定的介面。  
  
```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]用來建構的介面識別項的文字。  
  
### <a name="remarks"></a>備註  
 若要防止在特定情況下使用的介面，您可以使用這個巨集。 比方說，您可以將這個巨集插入您的 COM 對應前`COM_INTERFACE_ENTRY_AGGREGATE_BLIND`防止介面查詢轉寄到內部未知的彙總。  
  
 介面的 IID，就會建構，加上*x*到`IID_`。 例如，如果*x*是`IPersistStorage`，將 IID `IID_IPersistStorage`。  
  
 請參閱[COM_INTERFACE_ENTRY 巨集](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)備註 COM 對應項目。  
  
##  <a name="a-nameendcommapa--endcommap"></a><a name="end_com_map"></a>END_COM_MAP  
 結束您的 COM 介面對應的定義。  
  
```
END_COM_MAP()
```  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)   
 [COM 對應全域函式](../../atl/reference/com-map-global-functions.md)

