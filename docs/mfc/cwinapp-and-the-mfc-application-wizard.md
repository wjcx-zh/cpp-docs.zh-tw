---
title: CWinApp 和 MFC 應用程式精靈 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d40f314c7717d2e69b2b4802bf9c2c5468511db5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341257"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp 和 MFC 應用程式精靈
MFC 應用程式精靈建立基本架構應用程式時, 宣告應用程式類別衍生自[CWinApp](../mfc/reference/cwinapp-class.md)。 MFC 應用程式精靈也會產生實作檔包含下列項目：  
  
-   應用程式類別的訊息對應。  
  
-   空的類別建構函式。  
  
-   變數宣告和物件的類別。  
  
-   標準實作您`InitInstance`成員函式。  
  
 應用程式類別位於專案的標頭和主要原始程式檔。 類別和建立檔案的名稱會根據您在 MFC 應用程式精靈中提供的專案名稱。 若要檢視這些類別的程式碼的最簡單方式是透過[類別檢視](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)。  
  
 標準實作和訊息對應提供足夠用於許多用途，但您可以視需要修改它們。 這些實作最有趣的是`InitInstance`成員函式。 一般來說，您會加入程式碼的架構實作`InitInstance`。  
  
## <a name="see-also"></a>另請參閱  
 [CWinApp： 應用程式類別](../mfc/cwinapp-the-application-class.md)   
 [可覆寫的 CWinApp 成員函式](../mfc/overridable-cwinapp-member-functions.md)   
 [特殊 CWinApp 服務](../mfc/special-cwinapp-services.md)

