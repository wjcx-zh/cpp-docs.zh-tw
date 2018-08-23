---
title: 'Ftmbase:: Marshalinterface 方法 |Microsoft Docs'
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
ms.openlocfilehash: a95521123a87a6ae68ce9f923779c1a6ceda4ccf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599707"
---
# <a name="ftmbasemarshalinterface-method"></a>FtmBase::MarshalInterface 方法

寫入資料流來初始化 proxy 物件中某些用戶端處理序所需的資料。

## <a name="syntax"></a>語法

```cpp
STDMETHODIMP MarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags
) override;
```

### <a name="parameters"></a>參數

*pStm*  
要封送處理期間使用的資料流的指標。

*riid*  
要封送處理介面識別項參考。 此介面必須衍生自`IUnknown`介面。

*pv*  
要封送處理; 之介面指標的指標如果呼叫端所需的介面沒有指標，則可以是 NULL。

*dwDestContext*  
指定的介面所在解除封送處理的目的端內容。

指定一或多個 MSHCTX 列舉值。

解封送處理，可能會發生在目前的處理序 (MSHCTX_LOCAL) 的同一部電腦上的另一個處理序或目前的處理序 (MSHCTX_INPROC) 的另一個 apartment 中。

*pvDestContext*  
保留以備將來之用；必須為零。

*mshlflags*  
指定要封送處理的資料是否要傳送回用戶端程序 — 一般的情況下，或寫入全域的資料表，其中要擷取多個用戶端。

## <a name="return-value"></a>傳回值

介面指標封送處理成功地傳回 S_OK。

E_NOINTERFACE 不支援指定的介面。

STG_E_MEDIUMFULL 資料流已滿。

E_FAIL 作業失敗。

## <a name="requirements"></a>需求

**標頭：** ftm.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[FtmBase 類別](../windows/ftmbase-class.md)