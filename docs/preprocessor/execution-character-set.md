---
title: "execution_character_set |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
dev_langs: C++
helpviewer_keywords: pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1064f5cf97ba6b919e718c60c8346e86d643ced
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="executioncharacterset"></a>execution_character_set
指定執行字元集，用於字串和字元常值。 這個指示詞不需要加上 u8 前置詞的常值。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma execution_character_set("target")  
```  
  
#### <a name="parameters"></a>參數  
 `target`  
 指定的目標執行字元集。 目前唯一的目標執行支援的設定為"utf-8"。  
  
## <a name="remarks"></a>備註  
 此編譯器指示詞已過時從 Visual Studio 2015 Update 2 開始。 我們建議您改用**/execution-charset:utf-8**或**/utf-8**編譯器選項，以及使用`u8`窄字元和字串常值包含延伸的前置字元字元。 如需有關`u8`首碼，請參閱[字串和字元常值](../cpp/string-and-character-literals-cpp.md)。 如需編譯器選項的詳細資訊，請參閱[/execution-charset （設定執行字元集）](../build/reference/execution-charset-set-execution-character-set.md)和[/utf-8 （設定來源和可執行檔為 utf-8 字元集）](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)。  
  
 `#pragma execution_character_set("utf-8")`指示詞會指示編譯器為 utf-8 編碼窄字元和窄字串常值，在原始程式碼中的，可執行檔中。 此輸出的編碼方式無關的來源檔案使用的編碼方式。  
  
 根據預設，編譯器將使用目前的字碼頁為執行字元集編碼窄字元和窄字串。 這表示目前的字碼頁的範圍以外的 Unicode 或 DBCS 字元常值中會轉換成預設的取代字元在輸出中。 Unicode 和 DBCS 字元會截斷成其低序位位元組。 這是幾乎肯定不預期。 您可以指定使用 utf-8 編碼方式的原始程式檔中的常值`u8`前置詞。 編譯器會保持不變的輸出來傳遞這些 utf-8 編碼的字串。 使用 u8 前置詞的半形字元常值必須符合在一個位元組，或被截斷輸出。  
  
 根據預設，Visual Studio 會使用目前的字碼頁，為用來解譯您的原始程式碼輸出的來源字元集。 在讀取檔案時，Visual Studio 會將它解譯會根據目前的字碼頁除非已設定的檔案的字碼頁，或偵測檔案的開頭到位元組順序標示 (BOM) 或 utf-16 字元。 由於 utf-8 無法設定為目前的字碼頁，自動偵測遇到原始程式檔編碼為 utf-8 無 BOM 時，Visual Studio 會假設它們使用目前的字碼頁來進行編碼。 原始程式檔中會超出範圍的指定或自動偵測的字碼頁可能會導致編譯器警告和錯誤的字元。  
  
## <a name="see-also"></a>請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [/execution-charset (設定執行 Character Set)](../build/reference/execution-charset-set-execution-character-set.md)   
 [/utf-8 （設定來源和可執行檔字元集為 utf-8）](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)