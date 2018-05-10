---
title: 展開萬用字元引數 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69d7a9fc75e23a03e4db232bc798c89f89083e62
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="expanding-wildcard-arguments"></a>展開萬用字元引數
**Microsoft 特定的**  
  
 執行 C 程式時，您可以在命令列上使用問號 (?) 和星號 (*) 這兩種萬用字元來指定檔案名稱和路徑引數。  
  
 預設不會展開命令列引數中的萬用字元。 您可藉由連結 setargv.obj 或 wsetargv.obj 檔案，將一般引數向量 `argv` 載入常式取代為可展開萬用字元的版本。 如果您的程式使用 `main` 函式，則會與 setargv.obj 連結。如果您的程式使用 `wmain` 函式，則會與 wsetargv.obj 連結。這兩種情況都有對等的行為。  
  
 若要與 setargv.obj 或 wsetargv.obj 連結，請使用 **/link** 選項。 例如:   
  
 **cl example.c /link setargv.obj**  
  
 展開萬用字元的方法與展開作業系統命令的方法相同 (如果您不熟悉萬用字元，請參閱作業系統的使用者指南)。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [連結選項](../c-runtime-library/link-options.md)   
 [main 函式和程式執行](../c-language/main-function-and-program-execution.md)