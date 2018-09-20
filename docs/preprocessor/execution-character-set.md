---
title: execution_character_set |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
dev_langs:
- C++
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a387b051bbecedd1c6c4dba8fc3881a3c1f3a4b9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446812"
---
# <a name="executioncharacterset"></a>execution_character_set
指定執行字元集，用於字串和字元常值。 常值標記為 u8 前置詞，就不需要此指示詞。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma execution_character_set("target")  
```  
  
### <a name="parameters"></a>參數  
*目標*  
指定目標執行字元集。 目前僅支援設定的目標執行為"utf-8"。  
  
## <a name="remarks"></a>備註  
 
此編譯器指示詞已過時開始在 Visual Studio 2015 Update 2。 我們建議您改用`/execution-charset:utf-8`或是`/utf-8`編譯器選項，以及使用`u8`上窄字元和字串常值包含擴充的字元的前置詞。 如需詳細資訊`u8`前置詞，請參閱 < [String and Character Literals](../cpp/string-and-character-literals-cpp.md)。 如需編譯器選項的詳細資訊，請參閱[（設定執行字元集） 的 /execution-charset](../build/reference/execution-charset-set-execution-character-set.md)並[/utf-8 （將來源和可執行檔字元集為 utf-8）](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)。  
  
`#pragma execution_character_set("utf-8")`指示詞會指示編譯器在可執行檔中將窄字元和窄字串常值程式碼中編碼為 utf-8。 此輸出編碼方式無關的來源檔案使用的編碼方式。  
  
根據預設，編譯器會使用目前的字碼頁為執行字元集編碼窄字元和窄字串。 這表示目前的字碼頁的範圍以外的 Unicode 或 DBCS 字元常值會轉換成預設的取代字元在輸出中。 Unicode 和 DBCS 字元會截斷成其低序位位元組。 這是幾乎肯定不是您預期。 您可以指定 使用 utf-8 編碼方式的原始程式檔中的常值`u8`前置詞。 編譯器會將這些 utf-8 編碼的字串傳遞至輸出不會變更。 使用 u8 前置詞的窄字元常值必須符合一個位元組，或就會截斷輸出。  
  
根據預設，Visual Studio 會使用目前的字碼頁，為用來解譯您的原始程式碼輸出的來源字元集。 在讀取檔案時，Visual Studio 會將它解譯根據目前的字碼頁除非已設定的檔案的字碼頁，或是將位元組順序標記 (BOM) 或 utf-16 字元會偵測到檔案開頭。 因為 utf-8 無法設定為目前的字碼頁，自動偵測遇到不具有 BOM 的 utf-8 編碼的原始程式檔時，Visual Studio 會假設它們被編碼使用目前的字碼頁。 原始程式檔中會超出範圍的指定或自動偵測到可能會導致編譯器警告和錯誤的字碼頁的字元。  
  
## <a name="see-also"></a>另請參閱  
 
[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[/execution-charset （設定執行字元集）](../build/reference/execution-charset-set-execution-character-set.md)<br/>
[/utf-8 (將來源和可執行檔字元集設定為 UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)