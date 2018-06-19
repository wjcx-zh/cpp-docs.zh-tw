---
title: 使用 wmain 取代 main |Microsoft 文件
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
ms.openlocfilehash: 1f8f916fd6716678218b1b9b3d5d8b2e21a37c29
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422198"
---
# <a name="using-wmain-instead-of-main"></a>使用 wmain 取代 main
## <a name="microsoft-specific"></a>Microsoft 特定的  
 在 Unicode 程式設計模型中，您可以定義寬字元版本的 **main** 函式。 使用**wmain**而不是**主要**如果您想要撰寫遵守 Unicode 規格的可攜式程式碼。  
  
 您可以使用類似於 **main**的格式將形式參數宣告為 **wmain**。 然後您可以傳遞寬字元引數以及 (選擇性的) 一個指向程式的寬字元環境指標。 **wmain** 的 `argv` 與 `envp` 參數都是 `wchar_t*` 類型。  
  
 如果您的程式使用**主要**函式，建立多位元組字元環境在程式啟動的作業系統。 只有在需要時才建立環境的寬字元複本 (例如，藉由呼叫[_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)或[_wputenv](../c-runtime-library/reference/putenv-wputenv.md)函式)。 在第一次呼叫 `_wputenv` 時，或在第一次呼叫 `_wgetenv` 時，如果 MBCS 環境已經存在，則會建立對應的寬字元字串環境，然後再由 `_wenviron` 全域變數 (是 `_environ` 全域變數的寬字元版本) 指向該變數。 此時會同時存在兩個環境 (MBCS 和 Unicode) 的複本，並由作業系統在整個程式存留期裡進行維護。  
  
 同樣地，如果您的程式使用**wmain**函式，第一次呼叫建立 MBCS (ASCII) 環境時`_putenv`或`getenv`，並指向`_environ`全域變數。  
  
 如需有關 MBCS 環境的詳細資訊，請參閱[單一位元組和多位元組字元集](../c-runtime-library/single-byte-and-multibyte-character-sets.md)中*執行階段程式庫參考。*  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)