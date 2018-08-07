---
title: 'Ftmbase:: Getmarshalsizemax 方法 |Microsoft Docs'
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
ms.openlocfilehash: c39c313f06bb4dd1f4dbc095df159a38625e9db8
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570210"
---
# <a name="ftmbasegetmarshalsizemax-method"></a>FtmBase::GetMarshalSizeMax 方法
取得指定的物件上指定的介面指標封送處理所需的位元組數目上限。  
  
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
  
### <a name="parameters"></a>參數  
 *riid*  
 要封送處理介面識別項參考。  
  
 *pv*  
 要封送處理; 介面指標可以是 NULL。  
  
 *dwDestContext*  
 指定的介面所在解除封送處理的目的端內容。  
  
 指定一或多個 MSHCTX 列舉值。  
  
 目前，解封送處理可能會發生在另一個 apartment，目前的處理序 (MSHCTX_INPROC) 或在目前的處理序 (MSHCTX_LOCAL) 的同一部電腦上的另一個處理序中。  
  
 *pvDestContext*  
 保留供未來使用;必須是 NULL。  
  
 *mshlflags*  
 旗標，指出要封送處理的資料是否要傳送回用戶端程序 — 一般的情況下，或寫入全域的資料表，其中要擷取多個用戶端。 指定一或多個 MSHLFLAGS 列舉值。  
  
 *pSize*  
 這項作業完成時，指標要封送處理的資料流寫入的資料量上限。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為 S_OK否則 E_FAIL 或 E_NOINTERFACE。  
  
## <a name="requirements"></a>需求  
 **標頭：** ftm.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [FtmBase 類別](../windows/ftmbase-class.md)