---
title: nullptr |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- nullptr_cpp
dev_langs:
- C++
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd7d7c9ccf70286040d06e7e01400299b806157e
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940970"
---
# <a name="nullptr"></a>nullptr
指定類型為 `std::nullptr_t` 的 Null 指標常數，此指標常數可以轉換成任何原始指標類型。  雖然您可以使用關鍵字**nullptr**不含任何標頭中，如果您的程式碼會使用型別`std::nullptr_t`，則您必須定義它所包含的標頭`<cstddef>`。  
  
> [!NOTE]
>  **Nullptr**關鍵字也會定義在 C + + /cli 適用於 CLI 管理程式碼應用程式，而且不能使用 ISO 標準 c + + 關鍵字互換。 如果您的程式碼可以使用編譯[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項，以 managed 程式碼為目標，然後使用`__nullptr`任何一行您必須保證編譯器會使用原生 c + + 解譯的程式碼中。 如需詳細資訊，請參閱 < [nullptr](../windows/nullptr-cpp-component-extensions.md)。  
  
## <a name="remarks"></a>備註  
 請避免使用 NULL 或零 (`0`) 為 null 指標常數;**nullptr**比較不容易誤用，而且在大部分情況下，效果更好。  例如，若使用 `func(std::pair<const char *, double>)`，呼叫 `func(std::make_pair(NULL, 3.14))` 就會造成編譯器錯誤。  巨集 NULL 會展開為 `0`，因此呼叫 `std::make_pair(0, 3.14)` 會傳回 `std::pair<int, double>` (不可轉換為 func() 的 `std::pair<const char *, double>` 參數類型)。  呼叫 `func(std::make_pair(nullptr, 3.14))` 可以成功編譯，因為 `std::make_pair(nullptr, 3.14)` 會傳回 `std::pair<std::nullptr_t, double>` (可轉換為 `std::pair<const char *, double>`)。  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)