---
title: 使用 wmain 取代 main |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- wmain
dev_langs:
- C++
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1be93b3c8d011fb34c6259fe5f044a9c463e4b20
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941209"
---
# <a name="using-wmain-instead-of-main"></a>使用 wmain 取代 main
## <a name="microsoft-specific"></a>Microsoft 特定的  
 在 Unicode 程式設計模型中，您可以定義的寬字元版本`main`函式。 使用`wmain`而不是`main`如果您想要撰寫遵守 Unicode 規格的可攜式程式碼。  
  
 宣告型式參數`wmain`使用類似的格式來`main`。 然後您可以傳遞寬字元引數以及 (選擇性的) 一個指向程式的寬字元環境指標。 *Argv*並*envp*參數`wmain`屬於類型`wchar_t*`。  
  
 如果您的程式使用`main`函式，建立多位元組字元環境在程式啟動的作業系統。 只在需要時，會建立環境的寬字元複本 (如藉由呼叫[_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)或是[_wputenv](../c-runtime-library/reference/putenv-wputenv.md)函式)。 在第一次呼叫 `_wputenv` 時，或在第一次呼叫 `_wgetenv` 時，如果 MBCS 環境已經存在，則會建立對應的寬字元字串環境，然後再由 `_wenviron` 全域變數 (是 `_environ` 全域變數的寬字元版本) 指向該變數。 此時會同時存在兩個環境 (MBCS 和 Unicode) 的複本，並由作業系統在整個程式存留期裡進行維護。  
  
 同樣地，如果您的程式使用`wmain`函式的第一個呼叫建立 MBCS (ASCII) 環境時`_putenv`或`getenv`，並藉由指向`_environ`全域變數。  
  
 如需有關 MBCS 環境的詳細資訊，請參閱 <<c0> [ 單一位元組和多位元組字元集](../c-runtime-library/single-byte-and-multibyte-character-sets.md)在*執行階段程式庫參考。*  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)