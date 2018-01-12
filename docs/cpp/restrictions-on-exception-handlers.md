---
title: "例外狀況處理常式的限制 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f9e55ba9c36fdbc5f3c19e7ad81373599ab138e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="restrictions-on-exception-handlers"></a>例外狀況處理常式的限制
在程式碼中使用例外狀況處理常式的主要限制是，您不能使用 `goto` 陳述式跳入 `__try` 陳述式區塊。 您必須改為透過一般控制流程進入陳述式區塊。 您可以跳出 `__try` 陳述式區塊，並且依您選擇的方式將例外狀況處理常式巢狀化。  
  
## <a name="see-also"></a>請參閱  
 [撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)   
 [結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)