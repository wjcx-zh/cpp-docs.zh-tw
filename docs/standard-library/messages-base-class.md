---
title: "messages_base 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocmes/std::messages_base
dev_langs:
- C++
helpviewer_keywords:
- messages_base class
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: e95f92d910919ed0fc07943ff7b452ddd7d6b203
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="messagesbase-class"></a>messages_base 類別
基底類別，描述訊息目錄的 `int` 類型。  
  
## <a name="syntax"></a>語法  
  
```
struct messages_base : locale::facet {
    typedef int catalog;
    explicit messages_base(size_t _Refs = 0)
};
```  
  
## <a name="remarks"></a>備註  
 catalog 類型與描述可能從 messages:: [do_open](../standard-library/messages-class.md#do_open) 傳回之值的 `int` 類型同義。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



