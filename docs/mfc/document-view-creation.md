---
title: "建立文件檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- documents [MFC], creating
- views [MFC], and frame windows
- views [MFC], creating
- tables [MFC]
- MFC, views
- document/view architecture [MFC], creating document/view
- object creators
- MFC, documents
- tables [MFC], objects each MFC object creates
ms.assetid: bda14f41-ed50-439d-af9e-591174e7dd64
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c6997189f23ea7599dde0a1b19ba9f0ea350378d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="documentview-creation"></a>文件/檢視建立
架構會提供實作`New`和**開啟**命令 （和其他項目） 上**檔案**功能表。 建立新文件及其相關聯的檢視和框架視窗是應用程式物件、 文件範本，新建立的文件和框架視窗之間的合作式投入時間。 下表摘要說明哪些物件建立什麼。  
  
### <a name="object-creators"></a>物件建立者  
  
|建立者|建立|  
|-------------|-------------|  
|Application 物件|文件範本|  
|文件範本|文件|  
|文件範本|框架視窗|  
|框架視窗|檢視|  
  
## <a name="see-also"></a>請參閱  
 [文件範本和文件/檢視建立程序](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [建立文件範本](../mfc/document-template-creation.md)   
 [MFC 物件關聯性](../mfc/relationships-among-mfc-objects.md)   
 [建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)

