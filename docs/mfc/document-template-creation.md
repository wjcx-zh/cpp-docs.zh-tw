---
title: "文件範本建立 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 04950601a74b1ed3e44b236e1d07dcdff997eca6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="document-template-creation"></a>文件樣板建立
在回應中建立新文件時`New`或**開啟**命令**檔案**功能表上，文件範本也會建立新的框架視窗，以檢視文件。  
  
 文件範本建構函式會指定哪些類型的文件、 視窗和範本可以建立的檢視。 這取決於您傳遞至文件範本建構函式的引數。 下列程式碼說明如何建立[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)範例應用程式：  
  
 [!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/cpp/document-template-creation_1.cpp)]  
  
 新的指標`CMultiDocTemplate`物件作為引數[AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate)。 引數`CMultiDocTemplate`建構函式包含文件類型的功能表和快速鍵，相關聯的資源識別碼和三個用途[RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)巨集。 `RUNTIME_CLASS`傳回[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)命名為其引數的 c + + 類別的物件。 三個`CRuntimeClass`物件傳遞至文件範本建構函式提供文件建立程序期間建立的指定類別的新物件所需的資訊。 此範例示範建立的文件範本建立`CScribDoc`物件與`CScribView`附加的物件。 標準的 MDI 子框架視窗所包覆的檢視。  
  
## <a name="see-also"></a>請參閱  
 [文件範本和文件/檢視建立程序](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [文件/檢視建立](../mfc/document-view-creation.md)   
 [MFC 物件關聯性](../mfc/relationships-among-mfc-objects.md)   
 [建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)

