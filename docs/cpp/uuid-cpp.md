---
title: uuid （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- uuid_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b143def4d758307c6ce6737281bdca1097aaa8c5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="uuid-c"></a>uuid (C++)
**Microsoft 特定的**  
  
 編譯器會將 GUID 附加至使用 `uuid` 屬性宣告或定義 (僅限完整 COM 物件定義) 的類別或結構。  
  
## <a name="syntax"></a>語法  
  
```  
  
__declspec( uuid("ComObjectGUID") ) declarator  
```  
  
## <a name="remarks"></a>備註  
 `uuid` 屬性可接受字串做為其引數。 這個字串名稱以標準登錄格式，不論 GUID **{}** 分隔符號。 例如:   
  
```  
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;  
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;  
```  
  
 這個屬性可以在重新宣告中套用。 這可讓系統標頭提供介面的定義，例如**IUnknown**，並且在某些其他標頭中的重新宣告 (例如\<comdef.h >) 以提供 GUID。  
  
 關鍵字[__uuidof](../cpp/uuidof-operator.md)可以套用至擷取 GUID 附加至使用者定義類型的常數。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)