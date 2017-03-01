---
title: "封送處理全域函式 |Microsoft 文件"
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
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
caps.latest.revision: 19
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: dd4b8d50ec69974b7b2af29438b1657e1ce592b4
ms.lasthandoff: 02/24/2017

---
# <a name="marshaling-global-functions"></a>封送處理的全域函式
這些函式提供支援封送處理，並將封送處理資料轉換成介面指標。  
  
> [!IMPORTANT]
>  下表所列出的函數不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
|||  
|-|-|  
|[AtlFreeMarshalStream](#atlfreemarshalstream)|釋放封送處理資料和`IStream`指標。|  
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|建立新的資料流物件，並封送處理指定的介面指標。|  
|[AtlUnmarshalPtr](#atlunmarshalptr)|將資料流的封送處理資料轉換的介面指標。|  
  
##  <a name="a-nameatlfreemarshalstreama--atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a>AtlFreeMarshalStream  
 釋放資料流的封送處理資料，然後釋放資料流指標。  

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```  
  
### <a name="parameters"></a>參數  
 `pStream`  
 [in]指標`IStream`上用來封送處理的資料流介面。  
  
### <a name="example"></a>範例  
  請參閱範例[AtlMarshalPtrInProc](#atlmarshalptrinproc)。  
  
##  <a name="a-nameatlmarshalptrinproca--atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a>AtlMarshalPtrInProc  
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
 **MSHLFLAGS_TABLESTRONG**旗標設定，因此指標可以封送處理至多個資料流。 指標也可以解除封送處理多次。  
  
 如果封送處理會失敗，會釋放資料流指標。  
  
 `AtlMarshalPtrInProc`僅能在同處理序物件的指標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM&#50;](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]  
  
##  <a name="a-nameatlunmarshalptra--atlunmarshalptr"></a><a name="atlunmarshalptr"></a>AtlUnmarshalPtr  
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
 [out]解封送處理介面的指標。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="example"></a>範例  
  請參閱範例[AtlMarshalPtrInProc](#atlmarshalptrinproc)。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../atl/reference/atl-functions.md)

