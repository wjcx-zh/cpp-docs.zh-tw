---
title: "uuid （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- uuid_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c999b429cb789167eeb754b6f11a8b3d90c28642
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="uuid-c"></a>uuid (C++)
**Microsoft 特定的**  
  
 編譯器會將 GUID 附加至使用 `uuid` 屬性宣告或定義 (僅限完整 COM 物件定義) 的類別或結構。  
  
## <a name="syntax"></a>語法  
  
```  
  
__declspec( uuid("ComObjectGUID") ) declarator  
```  
  
## <a name="remarks"></a>備註  
 `uuid` 屬性可接受字串做為其引數。 這個字串名稱以標準登錄格式，不論 GUID **{}**分隔符號。 例如:   
  
```  
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;  
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;  
```  
  
 這個屬性可以在重新宣告中套用。 這可讓系統標頭提供介面的定義，例如**IUnknown**，並且在某些其他標頭中的重新宣告 (例如\<comdef.h >) 以提供 GUID。  
  
 關鍵字[__uuidof](../cpp/uuidof-operator.md)可以套用至擷取 GUID 附加至使用者定義類型的常數。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)