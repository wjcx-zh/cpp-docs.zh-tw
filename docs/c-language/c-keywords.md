---
title: "C 關鍵字 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2fd746124cdfc267267bc5d6803700cca507c34d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="c-keywords"></a>C 關鍵字
「關鍵字」是指對 C 編譯器有特殊意義的字詞。 在轉譯階段 7 和 8 中，識別項不能包含與 C 關鍵字相同的拼字和大小寫。 (請參閱《前置處理器參考》中的[轉譯階段](../preprocessor/phases-of-translation.md)描述。如需識別碼的詳細資訊，請參閱[識別碼](../c-language/c-identifiers.md))。C 語言使用下列關鍵字：  
  
|||||  
|-|-|-|-|  
|**auto**|**double**|**int**|**struct**|  
|**break**|**else**|**long**|**switch**|  
|**case**|**enum**|**register**|**typedef**|  
|**char**|**extern**|**return**|**union**|  
|**const**|**float**|**short**|**unsigned**|  
|**continue**|**for**|**signed**|**void**|  
|**default**|**goto**|**sizeof**|**volatile**|  
|**do**|**if**|**static**|**while**|  
  
 您無法重新定義關鍵字。 不過，您可以在編譯前，使用 C [前置處理器指示詞](../preprocessor/preprocessor-directives.md)指定要取代為關鍵字的文字。  
  
 **Microsoft 特定的**  
  
 ANSI C 標準允許保留具有兩個前置底線的識別項，供編譯器實作使用。 因此，Microsoft 的慣例就是在 Microsoft 專有關鍵字名稱前面加上雙底線。 這些字詞不可做為識別項名稱使用。 如需命名識別碼之 ANSI 規則的描述，包括使用雙底線，請參閱[識別碼](../c-language/c-identifiers.md)。  
  
 Microsoft C 編譯器可辨識下列關鍵字和特殊識別項：  
  
|||||  
|-|-|-|-|  
|**__asm**|**dllimport**2|**__int8**|**naked**2|  
|**__based**1|**__except**|**__int16**|**__stdcall**|  
|**__cdecl**|**__fastcall**|**__int32**|**thread**2|  
|**__declspec**|**__finally**|**__int64**|**__try**|  
|**dllexport**2|**__inline**|**__leave**||  
  
 1. **__based** 關鍵字用於 32 位元和 64 位元目標編譯時有所限制。  
  
 2. 這些是搭配 **__declspec** 使用時的特殊識別碼，在其他內容中使用則不受限制。  
  
 Microsoft 擴充功能預設為啟用。 為了確保您的程式可完整移植，您可以在編譯期間指定 /Za 選項 (適用於 ANSI 相容性編譯)，停用 Microsoft 擴充功能。 如果您這樣做，Microsoft 專有關鍵字就會停用。  
  
 在 Microsoft 擴充功能啟用時，您可以在程式中使用上面所列的關鍵字。 為了提供 ANSI 相容性，大部分關鍵字前面都會加上雙底線。 **dllexport**、**dllimport**、**naked** 和 **thread** 這四個例外狀況只會搭配 **__declspec** 使用，因此不需要前置雙底線。 為了提供回溯相容性，仍支援其餘關鍵字的單一底線版本。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [C 的元素](../c-language/elements-of-c.md)