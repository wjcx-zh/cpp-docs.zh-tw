---
title: 'Ftmbase:: Marshalinterface 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- MarshalInterface method
ms.assetid: fc8421b4-06e4-4925-b908-c285fe4790d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc22b83aee62b03ec5e664d08440b00718325272
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="ftmbasemarshalinterface-method"></a>FtmBase::MarshalInterface 方法
初始化 proxy 物件，在某些用戶端處理序中的所需的資料寫入資料流。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHODIMP MarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags  
) override;  
```  
  
#### <a name="parameters"></a>參數  
 `pStm`  
 封送處理期間所要使用資料流指標。  
  
 `riid`  
 要封送處理介面的識別項參考。 此介面必須衍生自 IUnknown 介面。  
  
 `pv`  
 指標的介面指標無法封送處理。如果呼叫端所需的介面沒有指標，可以是 NULL。  
  
 `dwDestContext`  
 要解除封送處理指定的介面則為其中的目的端內容。  
  
 指定一或多個 MSHCTX 列舉值。  
  
 解封送處理，可能會發生在目前的處理序 (MSHCTX_INPROC) 的另一個 apartment 或目前的處理序 (MSHCTX_LOCAL) 的同一部電腦上的另一個處理序。  
  
 `pvDestContext`  
 保留以備將來之用；必須為零。  
  
 `mshlflags`  
 指定要傳送回用戶端處理序是否要封送處理資料 — 一般的情況下，或寫入全域的資料表，其中多個用戶端擷取。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 介面指標封送處理成功。  
  
 E_NOINTERFACE  
 不支援指定的介面。  
  
 STG_E_MEDIUMFULL  
 資料流已滿。  
  
 E_FAIL  
 作業失敗。  
  
## <a name="requirements"></a>需求  
 **標頭：** ftm.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [FtmBase 類別](../windows/ftmbase-class.md)