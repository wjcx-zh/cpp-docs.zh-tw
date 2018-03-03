---
title: "封送處理全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
dev_langs:
- C++
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a12f719d2cb893a5d2989a80f5fe09a5b49aeca2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="marshaling-global-functions"></a>封送處理的全域函式
這些函式提供封送處理，並將封送處理資料轉換成介面指標的支援。  
  
> [!IMPORTANT]
>  下表所列出的函數不能在 Windows 執行階段中執行的應用程式。  
  
|||  
|-|-|  
|[AtlFreeMarshalStream](#atlfreemarshalstream)|釋放的封送處理資料和`IStream`指標。|  
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|建立新的資料流物件，並封送處理指定的介面指標。|  
|[AtlUnmarshalPtr](#atlunmarshalptr)|將資料流的封送處理資料轉換成的介面指標。|  

## <a name="requirements"></a>需求：
**標頭：** atlbase.h
  
##  <a name="atlfreemarshalstream"></a>AtlFreeMarshalStream  
 釋放資料流的封送處理資料，然後釋放資料流指標。  

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```  
  
### <a name="parameters"></a>參數  
 `pStream`  
 [in]指標`IStream`上用來封送處理的資料流介面。  
  
### <a name="example"></a>範例  
  請參閱範例的[AtlMarshalPtrInProc](#atlmarshalptrinproc)。  
  
##  <a name="atlmarshalptrinproc"></a>AtlMarshalPtrInProc  
 建立新的資料流物件、將 Proxy 的 CLSID 寫入資料流，並且藉由將初始化 Proxy 所需的資料寫入資料流的方式封送處理指定的介面指標。  
  
```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 [in]要封送處理介面的指標。  
  
 `iid`  
 [in]封送處理介面的 GUID。  
  
 `ppStream`  
 [out]指標`IStream`上用來封送處理的新資料流物件的介面。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 **MSHLFLAGS_TABLESTRONG**讓指標可以封送處理至多個資料流，設定旗標。 指標也可以解除封送處理多次。  
  
 如果封送處理會失敗，則會釋放資料流指標。  
  
 `AtlMarshalPtrInProc`僅能在同處理序物件的指標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]  
  
##  <a name="atlunmarshalptr"></a>AtlUnmarshalPtr  
 將資料流的封送處理資料轉換成可供用戶端使用的介面指標。  
   
```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```  
  
### <a name="parameters"></a>參數  
 `pStream`  
 [in]正在 marshaling 資料流的指標。  
  
 `iid`  
 [in]正在 marshaling 介面的 GUID。  
  
 `ppUnk`  
 [out]解除封送處理介面的指標。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="example"></a>範例  
  請參閱範例的[AtlMarshalPtrInProc](#atlmarshalptrinproc)。  
  
## <a name="see-also"></a>請參閱  
 [函式](../../atl/reference/atl-functions.md)
