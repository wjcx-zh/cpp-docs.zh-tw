---
title: main： 程式啟動 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
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
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fbb3d19101358012df795000907a0b3e8139601
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="main-program-startup"></a>main：程式啟動
名為的特殊函式`main`是執行所有的 C 和 c + + 程式的起點。 如果您要撰寫的程式碼遵守 [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] 程式設計模型，您可以使用 `wmain` (寬字元版本的 `main`)。  
  
 編譯器不會預先定義 `main` 函式。 必須在程式文字中提供這個函式。  
  
 `main` 的宣告語法是  
  
```  
int main();  
```  
  
 或者可以選擇  
  
```  
int main(int argc, char *argv[], char *envp[]);  
```  
  
## <a name="microsoft-specific"></a>Microsoft 特定的  
 `wmain` 的宣告語法如下：  
  
```  
int wmain( );  
```  
  
 或者可以選擇  
  
```  
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);  
```  
  
 您也可以使用在 TCHAR.h 中定義的 `_tmain`。 除非定義 _UNICODE，否則 `_tmain` 會解析成 `main`。 在此情況下，`_tmain` 會解析成 `wmain`。  
  
 或者可以將 `main` 和 `wmain` 函式宣告為傳回 `void` (無傳回值)。 如果您宣告`main`或`wmain`為傳回`void`，您也無法使用父處理序或作業系統傳回的結束代碼[傳回](../cpp/return-statement-in-program-termination-cpp.md)陳述式。 要傳回的結束代碼時`main`或`wmain`宣告為`void`，您必須使用[結束](../cpp/exit-function.md)函式。  
  
**結束 Microsoft 特定的**  
 `argc` 和 `argv` 的類型是由語言定義。 `argc`、`argv` 和 `envp` 都是傳統名稱，但編譯器不需使用。 如需詳細資訊和範例，請參閱[引數定義](../cpp/argument-definitions.md)。  
  
## <a name="see-also"></a>請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [使用 wmain 取代 main](../cpp/using-wmain-instead-of-main.md)   
 [main 函式限制](../cpp/main-function-restrictions.md)