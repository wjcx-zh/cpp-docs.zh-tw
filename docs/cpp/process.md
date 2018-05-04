---
title: 處理序 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- process_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8aa1ba2676ebbd04d1fc1a59d210d69efeab6658
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="process"></a>處理序
指定您的 Managed 應用程式處理序應該使用特定全域變數的單一複本、靜態成員變數，或在處理序中的所有應用程式定義域中共用的靜態區域變數。 這主要要與編譯時才能使用 **/clr: pure**，現在已被取代以及編譯器的未來版本將移除。 編譯時 **/clr**，全域和靜態變數是每個預設程序 (不需要使用`__declspec(process)`。  
  
 只有原生類型的全域變數、靜態成員變數或靜態區域變數可以使用 `__declspec(process)` 來標記。  
  
  
 `process` 當編譯時才有效[/clr](../build/reference/clr-common-language-runtime-compilation.md)。  
  
 如果您想每個應用程式定義域擁有自己的全域變數複本，請使用[appdomain](../cpp/appdomain.md)。  
  
 請參閱[應用程式定義域和 Visual c + +](../dotnet/application-domains-and-visual-cpp.md)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)