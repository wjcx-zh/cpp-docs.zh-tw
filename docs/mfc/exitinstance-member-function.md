---
title: "ExitInstance 成員函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: 
dev_langs: C++
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0dc1710bbb6efd5bc48aa0b640c8e05747dce2e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="exitinstance-member-function"></a>ExitInstance 成員函式
[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance)類別成員函式[CWinApp](../mfc/reference/cwinapp-class.md)一份您的應用程式終止時，通常是因為使用者結束應用程式每次呼叫。  
  
 如果您需要特別清除處理，例如釋放繪圖裝置介面 (Graphics Device，GDI) 資源或解除配置程式執行期間使用的記憶體，則可以覆寫 `ExitInstance`。 不過，如文件和檢視這類標準項目的清除則是由 Framework，以及其他針對這些特定物件執行特殊清除的可覆寫函式所提供。  
  
## <a name="see-also"></a>另請參閱  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)
