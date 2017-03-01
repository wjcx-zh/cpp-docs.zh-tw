---
title: "訊息對應巨集 (MFC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- message map macros
- Windows messages [C++], declaration
- demarcating Windows messages
- message maps [C++], macros
- message maps [C++], declaration and demarcation
- message mapping macros
- ranges, message map
- message map ranges
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
caps.latest.revision: 10
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
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: f890e0675be58c8e20e313bea54b4145e2ce0bf3
ms.lasthandoff: 02/24/2017

---
# <a name="message-map-macros-mfc"></a>訊息對應巨集 (MFC)
若要支援訊息對應，MFC 提供下列巨集：  
  
### <a name="message-map-declaration-and-demarcation-macros"></a>訊息對應宣告和分界巨集  
  
|||  
|-|-|  
|[DECLARE_MESSAGE_MAP](http://msdn.microsoft.com/library/c225e7e0-a81b-495c-97f9-3e0aa1f65036)|宣告的訊息對應會使用類別將訊息與函式對應 (必須在類別宣告中使用)。|  
|[BEGIN_MESSAGE_MAP](http://msdn.microsoft.com/library/d9201e18-04e0-4639-9810-f15768627fc2)|開始進行訊息對應的定義 (必須在類別實作中使用)。|  
|[END_MESSAGE_MAP](http://msdn.microsoft.com/library/40f611f1-a3b4-4097-b683-091bf7cfab8b)|結束訊息對應的定義 (必須在類別實作中使用)。|  
  
### <a name="message-mapping-macros"></a>訊息對應巨集  
  
|||  
|-|-|  
|[ON_COMMAND](http://msdn.microsoft.com/library/f24f8bda-2cf4-49d5-aa3d-6f2e6bb003f2)|指出哪些函式會處理指定的命令訊息。|  
|[ON_CONTROL](http://msdn.microsoft.com/library/2cb7ebdf-296b-4606-b191-3449835003db)|指出哪些函式會處理指定的控制項通知訊息。|  
|[ON_MESSAGE](http://msdn.microsoft.com/library/e2faeb13-9f6e-4c0d-9f6d-b2e141a0db1e)|指出哪些函式會處理使用者定義的訊息。|  
|[ON_OLECMD](http://msdn.microsoft.com/library/6c86327c-3d48-42ac-9dae-e0ccd3a81793)|指出哪些函式會處理來自 DocObject 或其容器的功能表命令。|  
|[ON_REGISTERED_MESSAGE](http://msdn.microsoft.com/library/93c1c068-ae8c-4e04-8a60-a603800ab57d)|指出哪些函式會處理已註冊的使用者定義訊息。|  
|[ON_REGISTERED_THREAD_MESSAGE](http://msdn.microsoft.com/library/3f598bc2-b2f0-410f-8ba0-7714502170f3)|指出當您擁有 `CWinThread` 類別時，哪些函式會處理已註冊的使用者定義訊息。|  
|[ON_THREAD_MESSAGE](http://msdn.microsoft.com/library/f718f47a-d5b1-4514-914b-e3fe2d919003)|指出當您擁有 `CWinThread` 類別時，哪些函式會處理使用者定義的訊息。|  
|[ON_UPDATE_COMMAND_UI](http://msdn.microsoft.com/library/c4de3c21-2d2e-4b89-a4ce-d0c0e2d9edc4)|指出哪些函式會處理指定的使用者介面更新命令訊息。|  
  
### <a name="message-map-range-macros"></a>訊息對應範圍巨集  
  
|||  
|-|-|  
|[ON_COMMAND_RANGE](http://msdn.microsoft.com/library/c52719fc-dd6e-48c9-af79-383f48d608e0)|指出哪些函式會處理巨集的前兩個參數中指定之命令 ID 的範圍。|  
|[ON_UPDATE_COMMAND_UI_RANGE](http://msdn.microsoft.com/library/b7105bf1-44ad-4b00-b947-31478f964729)|指出哪些更新處理常式會處理在巨集前兩個參數中指定之命令 ID 的範圍。|  
|[ON_CONTROL_RANGE](http://msdn.microsoft.com/library/46f0e1bb-569b-4b8b-9b80-89701d1cd7fd)|指出哪些函式會處理來自在巨集的第二和第三個參數中指定之控制項 ID 範圍的通知。 第一個參數是一個控制項通知訊息，例如**BN_CLICKED**。|  
  
 如需訊息對應、 訊息對應宣告和分界巨集和訊息對應巨集的詳細資訊，請參閱[訊息對應](../../mfc/reference/message-maps-mfc.md)和[訊息處理和對應的主題](../../mfc/message-handling-and-mapping.md)。 如需訊息對應範圍的詳細資訊，請參閱[訊息對應範圍的處理常式](../../mfc/handlers-for-message-map-ranges.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息對應](../../mfc/reference/message-maps-mfc.md)



