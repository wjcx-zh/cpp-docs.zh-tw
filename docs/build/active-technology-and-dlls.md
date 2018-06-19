---
title: Active 技術和 Dll |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f5e0296b994f7944d5b26e98ba1b0545a03ec55b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360109"
---
# <a name="active-technology-and-dlls"></a>Active 技術和 DLL
Active 技術可讓物件伺服程式完整地於 DLL 內實作。 此類型的伺服器稱為同處理序伺服器。 MFC 不完全支援同處理序伺服器的視覺化編輯的所有功能主要是因為 Active 技術不提供伺服器連線到容器的主要訊息迴圈的方式。 MFC 需要存取容器應用程式的訊息迴圈，以處理快速鍵和閒置時間處理。  
  
 如果您正在撰寫 Automation 伺服程式，而且您的伺服器有無使用者介面，您可以將您的伺服器在處理序伺服器，並完全放入 DLL。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [Automation 伺服程式](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>另請參閱  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)