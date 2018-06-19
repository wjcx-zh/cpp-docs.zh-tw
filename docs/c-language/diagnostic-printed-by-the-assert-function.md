---
title: assert 函式所列印的診斷 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c219669d018dc8c4cb038e90dffd1137877f422
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382873"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>assert 函式所列印的診斷
**ANSI 4.2** 由 **assert** 函式所列印的診斷，以及該函式的終止行為  
  
 **assert** 函式會列印診斷訊息，並在運算式為 false (0) 時，呼叫 **abort** 常式。 診斷資訊格式如下  
  
 **判斷提示失敗**：*expression***，檔案* * *filename***，行* * *linenumber*  
  
 其中的 filename 是原始程式檔的名稱，而 linenumber 是原始程式檔中發生失敗的判斷提示行號。 如果運算式為 true (非零)，則不會採取任何動作。  
  
## <a name="see-also"></a>另請參閱  
 [程式庫函式](../c-language/library-functions.md)