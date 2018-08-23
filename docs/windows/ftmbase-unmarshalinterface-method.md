---
title: 'Ftmbase:: Unmarshalinterface 方法 |Microsoft Docs'
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
ms.openlocfilehash: ef462ae884aad4160ffbae1883485ac7e06d3aa5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610697"
---
# <a name="ftmbaseunmarshalinterface-method"></a>FtmBase::UnmarshalInterface 方法

初始化新建立的 proxy，並將該 proxy 傳回的介面指標。

## <a name="syntax"></a>語法

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>參數

*pStm*  
從中的介面指標是解除封送處理的資料流的指標。

*riid*  
要解除封送處理介面識別項參考。

*ppv*  
這項作業完成時，接收所要求的介面指標的指標變數的位址*riid*。 如果這項作業成功，**ppv*包含要解除封送處理介面的要求的介面指標。

## <a name="return-value"></a>傳回值

如果成功則為 S_OK否則 E_NOINTERFACE 或 E_FAIL。

## <a name="requirements"></a>需求

**標頭：** ftm.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[FtmBase 類別](../windows/ftmbase-class.md)