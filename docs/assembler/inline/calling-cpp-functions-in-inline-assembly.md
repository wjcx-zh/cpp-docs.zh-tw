---
title: 在內嵌組譯碼中呼叫 c + + 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffbd8038d240bc2ab0240d172d914790b6ca02ab
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049619"
---
# <a name="calling-c-functions-in-inline-assembly"></a>在內嵌組譯碼中呼叫 C++ 函式
## <a name="microsoft-specific"></a>Microsoft 特定的  
 `__asm` 區塊只能呼叫未多載的全域 C++ 函式。 如果您呼叫多載的全域 C++ 函式或 C ++ 成員函式，編譯器會發出錯誤。  
  
 您也可以呼叫任何以宣告的函式**extern"C"** 連結。 這可讓`__asm`區塊內呼叫 C 程式庫函式，因為所有標準標頭檔宣告具有程式庫函式的 c + + 程式**extern"C"** 連結。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [內嵌組合語言](../../assembler/inline/inline-assembler.md)