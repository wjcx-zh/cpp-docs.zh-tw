---
title: main： 程式啟動 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- vc.main.startup
- _tmain
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- entry points, program
- wmain function
- _tmain function
- startup code, main function
- main function, program startup
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41bc9c9771622b1778abc5bf86a8ebb6e67d3fbd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716896"
---
# <a name="main-program-startup"></a>main：程式啟動
名為的特殊函式**主要**是執行所有的 C 和 c + + 程式的起點。 如果您是撰寫的程式碼遵守 Unicode 程式設計模型，您可以使用`wmain`，這是寬字元版本**主要**。  
  
 **主要**函式不會預先定義的編譯器。 必須在程式文字中提供這個函式。  
  
 宣告語法**主要**是  
  
```cpp 
int main();  
```  
  
 或者可以選擇  
  
```cpp 
int main(int argc, char *argv[], char *envp[]);  
```  
  
## <a name="microsoft-specific"></a>Microsoft 特定的  
 `wmain` 的宣告語法如下：  
  
```cpp 
int wmain( );  
```  
  
 或者可以選擇  
  
```cpp 
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);  
```  
  
 您也可以使用在 TCHAR.h 中定義的 `_tmain`。 `_tmain` 會解析成**主要**除非定義 _UNICODE。 在此情況下，`_tmain` 會解析成 `wmain`。  
  
 或者，**主要**並`wmain`函式可以宣告為傳回**void** （沒有傳回值）。 如果您宣告**主要**或是`wmain`傳回**void**，您也無法使用父處理序或作業系統傳回的結束代碼[傳回](../cpp/return-statement-in-program-termination-cpp.md)陳述式。 傳回結束代碼時**主要**或是`wmain`宣告為**void**，您必須使用[結束](../cpp/exit-function.md)函式。  
  
**結束 Microsoft 專屬**

 `argc` 和 `argv` 的類型是由語言定義。 `argc`、`argv` 和 `envp` 都是傳統名稱，但編譯器不需使用。 如需詳細資訊和範例，請參閱 <<c0> [ 引數定義](../cpp/argument-definitions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [使用 wmain 取代 main](../cpp/using-wmain-instead-of-main.md)   
 [main 函式限制](../cpp/main-function-restrictions.md)   
 [剖析 C++ 命令列引數](../cpp/parsing-cpp-command-line-arguments.md)