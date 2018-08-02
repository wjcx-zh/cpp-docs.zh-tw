---
title: 例外狀況處理常式的限制 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8775f752a541d2a250e9c1c5a0c325b684335988
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464596"
---
# <a name="restrictions-on-exception-handlers"></a>例外狀況處理常式的限制
程式碼中使用例外狀況處理常式的主要限制是，您無法使用**goto**陳述式跳入 **__try**陳述式區塊。 您必須改為透過一般控制流程進入陳述式區塊。 您可以跳出 **__try**陳述式區塊和巢狀例外狀況處理常式，如您所選擇。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)   
 [結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)