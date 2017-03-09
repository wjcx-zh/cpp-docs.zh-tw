---
title: "加強性 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 12424d6d233c1c109cb246b6c5b520f2ef12539e
ms.lasthandoff: 02/24/2017

---
# <a name="robustness"></a>加強性
使用下列 C 執行階段程式庫函式加強您的程式。  
  
### <a name="run-time-robustness-functions"></a>執行階段加強性函式  
  
|函式|用法|.NET Framework 同等|  
|--------------|---------|-------------------------------|  
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|若 `new` 運算子無法配置記憶體，則將控制項傳送至您的錯誤處理機制。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|以 C++ 類型化例外狀況處理 Win32 例外狀況 (C 結構化例外狀況)。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|安裝要由 [terminate](../c-runtime-library/reference/terminate-crt.md) 呼叫的專屬中止函式。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|安裝要由 [unexpected](../c-runtime-library/reference/unexpected-crt.md) 呼叫的專屬中止函式。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
  
## <a name="see-also"></a>另請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [SetUnhandledExceptionFilter](http://msdn.microsoft.com/library/windows/desktop/ms680634.aspx)
