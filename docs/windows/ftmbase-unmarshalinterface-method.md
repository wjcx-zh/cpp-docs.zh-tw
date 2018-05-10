---
title: 'Ftmbase:: Unmarshalinterface 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- UnmarshalInterface method
ms.assetid: 6850a621-e9a6-4001-bc1e-bd5d1b121adc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 964ce5cc33b51c54446874522317814279cdd960
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="ftmbaseunmarshalinterface-method"></a>FtmBase::UnmarshalInterface 方法
初始化新建立的 proxy，並傳回該 proxy 的介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHODIMP UnmarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __deref_out void **ppv  
) override;  
```  
  
#### <a name="parameters"></a>參數  
 `pStm`  
 指標是解封送處理介面指標的串流。  
  
 `riid`  
 參考要解除封送處理介面的識別碼。  
  
 `ppv`  
 這項作業完成時，接收中要求的介面指標的指標變數的位址`riid`。 如果這項作業成功，*`ppv`包含要解除封送處理介面的要求的介面指標。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，E_NOINTERFACE 或 E_FAIL。  
  
## <a name="requirements"></a>需求  
 **標頭：** ftm.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [FtmBase 類別](../windows/ftmbase-class.md)