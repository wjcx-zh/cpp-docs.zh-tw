---
title: "使用結構化例外狀況處理 c + + |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, mixed with SEH
- structured exception handling, with C++ exception handling
ms.assetid: ec34b528-8c26-4429-b24a-6a68553aaa91
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 8f9805479d7ee9589cfd0da8491b0344d0bd7de1
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="using-structured-exception-handling-with-c"></a>在 C++ 中使用結構化例外狀況處理
這些文章中所述的結構化例外狀況處理可搭配 C 和 C++ 原始程式檔。 不過，它不是專為 C++ 所設計，不建議使用。 使用 C++ 例外狀況處理可確保您的程式碼更具可移植性。 此外，C++ 例外狀況處理機制更有彈性，因為它可以處理任何類型的例外狀況。  
  
 Microsoft C++ 現在以 ANSI C++ 標準為基礎，可支援 C++ 例外狀況處理模型。 這個機制會自動處理堆疊回溯期間的區域物件解構。 如果您要撰寫容錯 C++ 程式碼，且想要實作例外狀況處理，強烈建議您使用 C++ 例外狀況處理，而不要使用結構化例外狀況處理  (請注意，如這些文章中所述，C++ 編譯器支援結構化例外狀況處理建構，但標準的 C 編譯器並不支援 C++ 例外狀況處理語法)。如需 c + + 例外狀況處理的詳細資訊，請參閱[c + + 例外狀況處理](../cpp/cpp-exception-handling.md)和*標註的 c + + 參考手冊*作者 Margaret Ellis 和 Bjarne Stroustrup。  
  
## <a name="see-also"></a>另請參閱  
 [結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
