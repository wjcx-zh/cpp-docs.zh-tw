---
title: FtmBase 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
dev_langs:
- C++
helpviewer_keywords:
- FtmBase class
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ed3e9b9e66f673a3d86ded7b3d576e1203db9595
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570557"
---
# <a name="ftmbase-class"></a>FtmBase 類別
代表無限制執行緒封送處理器物件。  
  
## <a name="syntax"></a>語法  
  
```  
class FtmBase : public Microsoft::WRL::Implements<  
   Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,   
   Microsoft::WRL::CloakedIid<IMarshal> >;  
```  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [RuntimeClass 類別](runtimeclass-class.md)。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[FtmBase::FtmBase 建構函式](../windows/ftmbase-ftmbase-constructor.md)|初始化的新執行個體**FtmBase**類別。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[FtmBase::CreateGlobalInterfaceTable 方法](../windows/ftmbase-createglobalinterfacetable-method.md)|建立全域介面表 (GIT)。|  
|[FtmBase::DisconnectObject 方法](../windows/ftmbase-disconnectobject-method.md)|強制釋放物件的所有外部連線。 物件的伺服器會呼叫這個方法之前關閉物件的實作。|  
|[FtmBase::GetMarshalSizeMax 方法](../windows/ftmbase-getmarshalsizemax-method.md)|取得指定的物件上指定的介面指標封送處理所需的位元組數目上限。|  
|[FtmBase::GetUnmarshalClass 方法](../windows/ftmbase-getunmarshalclass-method.md)|取得 COM 使用，找出包含對應的 proxy 程式碼的 DLL 的 CLSID。 COM 會載入此 DLL 來建立未初始化的執行個體的 proxy。|  
|[FtmBase::MarshalInterface 方法](../windows/ftmbase-marshalinterface-method.md)|寫入資料流來初始化 proxy 物件中某些用戶端處理序所需的資料。|  
|[FtmBase::ReleaseMarshalData 方法](../windows/ftmbase-releasemarshaldata-method.md)|終結封送處理的資料封包。|  
|[FtmBase::UnmarshalInterface 方法](../windows/ftmbase-unmarshalinterface-method.md)|初始化新建立的 proxy，並將該 proxy 傳回的介面指標。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[FtmBase::marshaller_ 資料成員](../windows/ftmbase-marshaller-data-member.md)|保留無限制執行緒封送處理器的參考。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `FtmBase`  
  
## <a name="requirements"></a>需求  
 **標頭：** ftm.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)