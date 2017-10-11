---
title: "處理序 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- process_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: d4f2500adaaa7941444b22d7ce548370fc370533
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="process"></a>處理序
指定您的 Managed 應用程式處理序應該使用特定全域變數的單一複本、靜態成員變數，或在處理序中的所有應用程式定義域中共用的靜態區域變數。 這主要是在編譯使用時才能使用**/clr: pure**，因為下**/clr： 純**全域和靜態變數是每個應用程式網域，根據預設。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。 編譯時**/clr**，全域和靜態變數是每個預設程序 (不需要使用`__declspec(process)`。  
  
 只有原生類型的全域變數、靜態成員變數或靜態區域變數可以使用 `__declspec(process)` 來標記。  
  
 編譯時**/clr: pure**，根據處理程序標示為的變數也必須宣告為`const`。 這可確保每個處理序的變數在某個應用程式定義域中不會遭到變更，也不會在其他應用程式定義域中產生未預期的結果。 主要用途的`__declspec(process)`是啟用的全域變數、 靜態成員變數或在靜態區域變數的編譯時期初始化**/clr: pure**。  
  
 `process`當編譯時才有效[/clr](../build/reference/clr-common-language-runtime-compilation.md)或**/clr: pure**和不正確，以編譯時**/clr: safe**。  
  
 如果您想每個應用程式定義域擁有自己的全域變數複本，請使用[appdomain](../cpp/appdomain.md)。  
  
 請參閱[應用程式定義域和 Visual c + +](../dotnet/application-domains-and-visual-cpp.md)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)
