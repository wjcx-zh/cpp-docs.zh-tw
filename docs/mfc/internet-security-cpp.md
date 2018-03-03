---
title: "網際網路安全性 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- code signing [MFC], Internet security
- sandboxing [MFC]
- digital signatures [MFC], Internet security
- code signing [MFC]
- Web application security [MFC]
- code access security [MFC], Internet security considerations
- security [MFC]
- security [MFC], Internet
- Internet applications [MFC], security
- Web application security [MFC], Internet security approaches
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a44e528e871d784c432730799c44ac91af465be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="internet-security-c"></a>網際網路安全性 (C++)
程式碼的安全性是開發人員和使用者的網際網路應用程式的主要問題。 會有危險： 惡意程式碼、 已遭竄改的程式碼和程式碼從未知的站台或多位作者。  
  
 開發網際網路時，有兩種基本安全性作法。 第一個稱為 「 沙箱 」。 這種方法，應用程式限制為一組特定的應用程式開發介面，並排除潛在危險的例如檔案 I/O 程式可能損毀使用者的電腦上的資料。 第二個被實作使用數位簽章。 這種方法稱為 「 shrinkwrap 」 的網際網路功能。 程式碼會驗證，而且使用私密/公開金鑰的主要技術簽章。 此程式碼執行之前，以確保程式碼是來自已知的已驗證來源和，程式碼未被改變已簽署之後驗證其數位簽章。  
  
 在第一個案例中，您信任應用程式將不會進行任何不良影響，以及您信任來源的應用程式。 第二、 數位簽章可用來確認真實性。 數位簽章是業界標準來識別，並提供有關程式碼的 「 發行者 」 的詳細資料。 它的技術根據標準，包括 RSA 和 X.509。 瀏覽器通常會允許使用者選擇是否要下載及執行未知來源的程式碼。  
  
  
## <a name="see-also"></a>請參閱  
 [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)   
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)

