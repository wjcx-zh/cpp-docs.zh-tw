---
title: 'Platform:: changedstateexception 類別 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ChangedStateException
- VCCORLIB/Platform::ChangedStateException::ChangedStateException
dev_langs:
- C++
helpviewer_keywords:
- Platform::ChangedStateException
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 029242a466b7fbac0d967596c114eb0ad45aa569
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603208"
---
# <a name="platformchangedstateexception-class"></a>Platform::ChangedStateException 類別
當物件的內部狀態已經變更時擲回，藉以讓方法的結果失效。  
  
## <a name="syntax"></a>語法  
  
```cpp  
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>備註  
 擲回這個例外狀況的一個例子是，在父集合變更後呼叫集合迭代器或集合檢視的方法時，藉以讓方法的結果失效。  
  
 如需詳細資訊，請參閱 [COMException](../cppcx/platform-comexception-class.md) 類別。  
  
### <a name="requirements"></a>需求  
 **最低支援用戶端：** Windows 8  
  
 **最低支援伺服器：** Windows Server 2012  
  
 **命名空間：** Platform  
  
 **中繼資料：** platform.winmd  
  
## <a name="see-also"></a>另請參閱  
 [Platform::COMException 類別](../cppcx/platform-comexception-class.md)