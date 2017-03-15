---
title: "例外狀況處理常式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.exceptions
dev_langs:
- C++
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
caps.latest.revision: 8
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
ms.openlocfilehash: fe4946a8d3785c6295cb7537de0a11e06cd7a1cc
ms.lasthandoff: 02/24/2017

---
# <a name="exception-handling-routines"></a>例外狀況處理常式
使用 C++ 例外狀況處理函式在程式執行期間從非預期的事件復原。  
  
### <a name="exception-handling-functions"></a>例外狀況處理函式  
  
|函式|用法|.NET Framework 同等|  
|--------------|---------|-------------------------------|  
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|以 C++ 類型化例外狀況處理 Win32 例外狀況 (C 結構化例外狀況)|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|安裝要由 `terminate` 呼叫的專屬終止常式|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|安裝要由 `unexpected` 呼叫的專屬終止函式|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[terminate](../c-runtime-library/reference/terminate-crt.md)|在擲回例外狀況之後，在某些情況下自動呼叫。 `terminate` 函式會呼叫 `abort` 或您使用 `set_terminate` 指定的函式|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[unexpected](../c-runtime-library/reference/unexpected-crt.md)|呼叫 `terminate` 或您使用 `set_unexpected` 指定的函式。 目前 Microsoft C++ 例外狀況處理實作中未使用 `unexpected`|[System::Exception 類別](https://msdn.microsoft.com/en-us/library/system.exception.aspx)|  
  
## <a name="see-also"></a>另請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
