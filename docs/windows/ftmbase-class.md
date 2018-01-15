---
title: "FtmBase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: ftm/Microsoft::WRL::FtmBase
dev_langs: C++
helpviewer_keywords: FtmBase class
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f56321b71642f9d615c4d85fd66f878b19e44485
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ftmbase-class"></a>FtmBase 類別
代表無限制執行緒封送處理器物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
class FtmBase : public Microsoft::WRL::Implements<  
   Microsoft::WRL::RuntimeClassFlags< WinRtClassicComMix >,   
   Microsoft::WRL::CloakedIid< IMarshal > >;  
```  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 MSDN Library 中的 < COM 參考 > 主題的 「 COM 介面"副主題"IMarshal 」 主題。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[FtmBase::FtmBase 建構函式](../windows/ftmbase-ftmbase-constructor.md)|初始化 FtmBase 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[FtmBase::CreateGlobalInterfaceTable 方法](../windows/ftmbase-createglobalinterfacetable-method.md)|建立全域介面表 (GIT)。|  
|[FtmBase::DisconnectObject 方法](../windows/ftmbase-disconnectobject-method.md)|強制釋放物件的所有外部連接。 物件的伺服器會呼叫這個方法之前關閉物件的實作。|  
|[FtmBase::GetMarshalSizeMax 方法](../windows/ftmbase-getmarshalsizemax-method.md)|取得要封送處理指定的介面指標上的指定物件所需的位元組數目上限。|  
|[FtmBase::GetUnmarshalClass 方法](../windows/ftmbase-getunmarshalclass-method.md)|取得 COM 使用，找出包含對應的 proxy 程式碼的 DLL 的 CLSID。 COM 載入此 DLL 來建立未初始化的執行個體的 proxy。|  
|[FtmBase::MarshalInterface 方法](../windows/ftmbase-marshalinterface-method.md)|初始化 proxy 物件，在某些用戶端處理序中的所需的資料寫入資料流。|  
|[FtmBase::ReleaseMarshalData 方法](../windows/ftmbase-releasemarshaldata-method.md)|終結封送處理的資料封包。|  
|[FtmBase::UnmarshalInterface 方法](../windows/ftmbase-unmarshalinterface-method.md)|初始化新建立的 proxy，並傳回該 proxy 的介面指標。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[FtmBase::marshaller_ 資料成員](../windows/ftmbase-marshaller-data-member.md)|保留無限制執行緒封送處理器的參考。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `FtmBase`  
  
## <a name="requirements"></a>需求  
 **標頭：** ftm.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)