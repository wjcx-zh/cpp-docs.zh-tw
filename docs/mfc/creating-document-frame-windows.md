---
title: "建立文件框架視窗 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9098026c1a38f8e60093415ba1c5a2b3678b64d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-document-frame-windows"></a>建立文件框架視窗
[文件/檢視建立](../mfc/document-view-creation.md)示範如何[CDocTemplate](../mfc/reference/cdoctemplate-class.md)物件協調建立框架視窗、 文件和檢視，和它們一起連接。 三個[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)引數`CDocTemplate`建構函式指定框架視窗、 文件和文件範本建立以動態方式以回應使用者命令，例如新的命令，在檔案上的檢視類別功能表或 MDI 視窗功能表的 [新視窗] 命令。 建立檢視和文件框架視窗時，文件範本會儲存這項資訊供日後使用。  
  
 如[RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)機制才能正常運作，您的衍生框架視窗類別必須宣告與[DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate)巨集。 這是因為架構需要建立文件框架視窗使用類別的動態建構機制`CObject`。  
  
 當使用者選擇建立文件的命令時，架構會呼叫文件範本來建立文件物件、 它的檢視和框架視窗會顯示在檢視時。 當它建立文件框架視窗時，文件範本會建立適當的類別的物件-的類別衍生自[CFrameWnd](../mfc/reference/cframewnd-class.md) SDI 應用程式，或從[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) mdi應用程式。 然後，架構會呼叫框架視窗物件的[LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)從資源取得其資訊，以及建立 Windows 視窗的成員函式。 架構會將視窗控制代碼附加至框架視窗物件。 然後它會做為文件框架視窗的子視窗建立檢視。  
  
 請小心決定[初始化時機](../mfc/when-to-initialize-cwnd-objects.md)您`CWnd`-衍生物件。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [從 CObject （動態建立的機制） 衍生類別](../mfc/deriving-a-class-from-cobject.md)  
  
-   [文件/檢視建立 （範本及建立框架視窗）](../mfc/document-view-creation.md)  
  
-   [終結框架視窗](../mfc/destroying-frame-windows.md)  
  
## <a name="see-also"></a>請參閱  
 [使用框架視窗](../mfc/using-frame-windows.md)

