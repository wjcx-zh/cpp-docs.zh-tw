---
title: "MFC ActiveX 控制項： 方法 |Microsoft 文件"
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
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8e3b343b13118930612e4adfed4c33a65a9e7be8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-methods"></a>MFC ActiveX 控制項：方法
ActiveX 控制項就會引發事件本身以及其控制項容器之間的通訊。 容器也可以透過方法和屬性溝通與控制項。 方法也會呼叫函式。  
  
 方法和屬性提供用於匯出的介面，由其他應用程式，例如 Automation 用戶端和 ActiveX 控制項容器。 如需 ActiveX 控制項屬性的詳細資訊，請參閱文章[MFC ActiveX 控制項： 屬性](../mfc/mfc-activex-controls-properties.md)。  
  
 方法也類似的用途及目的 c + + 類別的成員函式。 有兩種類型的控制項可以實作的方法： 內建和自訂。 類似於內建事件、 內建方法，是那些方法[COleControl](../mfc/reference/colecontrol-class.md)提供實作。 如需有關內建方法的詳細資訊，請參閱文章[MFC ActiveX 控制項： 加入內建方法](../mfc/mfc-activex-controls-adding-stock-methods.md)。 讓開發人員所定義的自訂方法可讓控制項的其他自訂。 如需詳細資訊，請參閱文章[MFC ActiveX 控制項： 加入自訂方法](../mfc/mfc-activex-controls-adding-custom-methods.md)。  
  
 Microsoft Foundation 類別庫 (MFC) 會實作一套機制，可讓您控制支援內建及自訂的方法。 第一個部分是類別`COleControl`。 衍生自`CWnd`，`COleControl`成員函式支援通用於所有的 ActiveX 控制項的內建方法。 第二個部分，此機制是分派對應。 分派對應如下的訊息對應。不過，而不是將函式對應至 Windows 訊息識別碼，分派對應會對應至 IDispatch ID 的虛擬成員函式。  
  
 要讓控制項適當支援各種方法，其類別必須宣告分派對應。 這會透過下列程式碼位於控制項類別標頭檔 (。H） 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/cpp/mfc-activex-controls-methods_1.h)]  
  
 分派對應的主要用途是類別的建立外部呼叫端 （例如容器） 和控制項成員函式實作的方法所使用的方法名稱之間的關聯性。 已宣告的分派對應之後，還需要在控制項的實作 (。CPP) 檔案。 下列程式碼定義的分派對應：  
  
 [!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]  
  
 如果您使用[MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)若要建立專案，這些線條已自動加入。 如果未使用 MFC ActiveX 控制項精靈，您必須手動加入這行。  
  
 下列文章中討論的詳細資料中的方法：  
  
-   [MFC ActiveX 控制項：新增內建方法](../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [MFC ActiveX 控制項：新增自訂方法](../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [MFC ActiveX 控制項：從方法傳回錯誤碼](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

