---
title: 建立檔視圖
ms.date: 11/04/2016
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
ms.openlocfilehash: 5441827188f5bff98638cc85cd29e2efd79f8ae8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620333"
---
# <a name="documentview-creation"></a>文件/檢視建立

此架構會在 [檔案 **] 功能表上**提供**新**的和 [**開啟**] 命令的執行（還有其他專案）。 建立新檔及其相關聯的視圖和框架視窗，是應用程式物件、檔範本、新建立的檔，以及新建立的框架視窗之間的合作工作。 下表摘要說明哪些物件會建立什麼。

### <a name="object-creators"></a>物件建立者

|建立者|會|
|-------------|-------------|
|應用程式物件|檔範本|
|檔範本|Document|
|檔範本|框架視窗|
|框架視窗|檢視|

## <a name="see-also"></a>另請參閱

[檔範本和檔/視圖建立程式](document-templates-and-the-document-view-creation-process.md)<br/>
[文件樣板建立](document-template-creation.md)<br/>
[MFC 物件關聯性](relationships-among-mfc-objects.md)<br/>
[建立新文件、視窗和檢視](creating-new-documents-windows-and-views.md)
