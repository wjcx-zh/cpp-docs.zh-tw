---
title: 'Dontusenewusemake:: Operator new 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- operator new operator
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59354062dded7792dca1cd84683bba64f6a64aa0
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571421"
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator new 運算子
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
#### <a name="parameters"></a>參數  
 *__unnamed0*  
 未命名的參數，指定要配置的記憶體位元組數目。  
  
 *放置*  
 要配置的類型。  
  
## <a name="return-value"></a>傳回值  
 可用來傳遞其他引數，如果您多載運算子**新**。  
  
## <a name="remarks"></a>備註  
 多載運算子**新**並且讓它無法使用於`RuntimeClass`。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [DontUseNewUseMake 類別](../windows/dontusenewusemake-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)