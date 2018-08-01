---
title: 處理程序 |Microsoft Docs
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
ms.openlocfilehash: fdad177231c02d2e6f6fad171ae1811ecb9ccc6c
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407178"
---
# <a name="process"></a>處理序

指定您的 Managed 應用程式處理序應該使用特定全域變數的單一複本、靜態成員變數，或在處理序中的所有應用程式定義域中共用的靜態區域變數。 這主要要用於進行編譯時 **/clr: pure**，這是 Visual Studio 2017 中已被取代，且不支援的 Visual Studio 2017 中。 進行編譯時 **/clr**，全域和靜態變數是每個處理序預設並不需要使用 **__declspec （process)**。

只有全域變數、 靜態成員變數或原生類型的靜態區域變數可以使用標記 **__declspec （process)**。

**處理程序**進行編譯時才有效[/clr](../build/reference/clr-common-language-runtime-compilation.md)。

如果您想要擁有自己的全域變數的每個應用程式定義域時，使用[appdomain](../cpp/appdomain.md)。

請參閱[應用程式定義域和 Visual c + +](../dotnet/application-domains-and-visual-cpp.md)如需詳細資訊。

## <a name="see-also"></a>另請參閱
 [__declspec](../cpp/declspec.md)  
 [關鍵字](../cpp/keywords-cpp.md)
