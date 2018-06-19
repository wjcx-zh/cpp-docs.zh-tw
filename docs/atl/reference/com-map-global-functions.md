---
title: 全域函式 COM 對應 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 509479a923203acd80eaac1ef90aa64125d208c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359875"
---
# <a name="com-map-global-functions"></a>COM 對應全域函式
這些函式 COM 對應提供支援**IUnknown**實作。  
  
|||  
|-|-|  
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|委派給**IUnknown**的非彙總的物件。|  
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|會產生有效率的程式碼來比較介面針對**IUnknown**。|  

  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  

##  <a name="atlinternalqueryinterface"></a>  AtlInternalQueryInterface  
 擷取所要求介面的指標。  
  
```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 `pThis`  
 [in]包含的介面公開至 COM 對應物件的指標`QueryInterface`。  
  
 `pEntries`  
 [in]陣列 **_ATL_INTMAP_ENTRY**存取的可用的介面對應的結構。  
  
 `iid`  
 [in]所要求介面的 GUID。  
  
 `ppvObject`  
 [out]中指定的介面指標的指標`iid`，或**NULL**如果找不到介面。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 `AtlInternalQueryInterface` 只處理 COM 對應表格中的介面。 如果您的物件彙總，`AtlInternalQueryInterface`不會不會委派給外部未知。 您可以將介面輸入到 COM 對應表格，使用巨集[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)或其中一個變數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]  
  
##  <a name="inlineisequaliunknown"></a>  InlineIsEqualIUnknown  
 呼叫此函式的特殊案例的測試**IUnknown**。  
  
```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```  
  
### <a name="parameters"></a>參數  
 *rguid1*  
 [in]要比較 GUID **IID_IUnknown**。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../atl/reference/atl-functions.md)   
 [COM 對應巨集](../../atl/reference/com-map-macros.md)
