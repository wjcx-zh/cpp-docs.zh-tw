---
title: 'Ftmbase:: Getunmarshalclass 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
dev_langs:
- C++
helpviewer_keywords:
- GetUnmarshalClass method
ms.assetid: 535fc539-5b97-4967-b158-f7568f13d341
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 167ad8537a11a0118c15b588b353f33775b5ab3a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644995"
---
# <a name="ftmbasegetunmarshalclass-method"></a>FtmBase::GetUnmarshalClass 方法
取得 COM 使用，找出包含對應的 proxy 程式碼的 DLL 的 CLSID。 COM 會載入此 DLL 來建立未初始化的執行個體的 proxy。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDMETHODIMP GetUnmarshalClass(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out CLSID *pCid  
) override;  
```  
  
### <a name="parameters"></a>參數  
 *riid*  
 要封送處理介面識別項參考。  
  
 *pv*  
 要封送處理; 介面指標如果呼叫端所需的介面沒有指標，則可以是 NULL。  
  
 *dwDestContext*  
 指定的介面所在解除封送處理的目的端內容。  
  
 指定一或多個 MSHCTX 列舉值。  
  
 解封送處理，可能會發生在目前的處理序 (MSHCTX_INPROC) 的另一個 apartment，或在目前的處理序 (MSHCTX_LOCAL) 的同一部電腦上的另一個處理序。  
  
 *pvDestContext*  
 保留供未來使用;必須是 NULL。  
  
 *mshlflags*  
 這項作業完成時，用來在用戶端處理序中建立 proxy 的 CLSID 指標。  
  
 *pCid*  
  
## <a name="return-value"></a>傳回值  
 如果成功則為 S_OK否則，S_FALSE。  
  
## <a name="requirements"></a>需求  
 **標頭：** ftm.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [FtmBase 類別](../windows/ftmbase-class.md)