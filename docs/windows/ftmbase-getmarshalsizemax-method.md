---
title: 'Ftmbase:: Getmarshalsizemax 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
dev_langs:
- C++
helpviewer_keywords:
- GetMarshalSizeMax method
ms.assetid: b416b1bf-c73e-45d5-abb8-04921c1a0c94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5a298e63bc67dadf33a5e653d0eecf165a530d82
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="ftmbasegetmarshalsizemax-method"></a>FtmBase::GetMarshalSizeMax 方法
取得要封送處理指定的介面指標上的指定物件所需的位元組數目上限。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHODIMP GetMarshalSizeMax(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out DWORD *pSize  
) override;  
```  
  
#### <a name="parameters"></a>參數  
 `riid`  
 要封送處理介面的識別項參考。  
  
 `pv`  
 介面指標無法封送處理。可以是 NULL。  
  
 `dwDestContext`  
 要解除封送處理指定的介面則為其中的目的端內容。  
  
 指定一或多個 MSHCTX 列舉值。  
  
 目前，解封送處理可能會發生在目前的處理序 (MSHCTX_INPROC) 的另一個 apartment 中或在目前的處理序 (MSHCTX_LOCAL) 的同一部電腦上的另一個處理序。  
  
 `pvDestContext`  
 保留供未來使用。必須是 NULL。  
  
 `mshlflags`  
 旗標，指出是否要傳送回用戶端處理序封送處理的資料 — 一般的情況下，或寫入全域的資料表，其中多個用戶端擷取。 指定一或多個 MSHLFLAGS 列舉值。  
  
 `pSize`  
 這項作業完成時，要寫入的封送處理的資料流的資料數量上限的指標。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，E_FAIL 或 E_NOINTERFACE。  
  
## <a name="requirements"></a>需求  
 **標頭：** ftm.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [FtmBase 類別](../windows/ftmbase-class.md)