---
title: "assert 函式所列印的診斷 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 243956f1d85b07b5d5b810ebfd112b2cbfe16242
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="diagnostic-printed-by-the-assert-function"></a>assert 函式所列印的診斷
**ANSI 4.2**：由 **assert** 函式所列印的診斷，以及該函式的終止行為  
  
 **assert** 函式會列印診斷訊息，並在運算式為 false (0) 時呼叫 **abort** 常式。 診斷資訊的格式如下  
  
 **判斷提示失敗**: *expression***，檔案** *filename***，行號** *linenumber*  
  
 其中 filename 是原始程式檔的名稱，而 linenumber 是原始程式檔中發生失敗的判斷提示行號。 如果運算式為 true (非零)，則不會採取任何動作。  
  
## <a name="see-also"></a>請參閱  
 [程式庫函式](../c-language/library-functions.md)