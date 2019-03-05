---
title: 文件-檢視建立
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
ms.openlocfilehash: b5f9b783e8e14744a816fd63b327ed95d9da8e8a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304943"
---
# <a name="documentview-creation"></a>文件/檢視建立

此架構提供的實作**新增**並**開啟**（還有其他） 上的命令**檔案**功能表。 建立新的文件及其相關聯的檢視和框架視窗會是應用程式物件、 文件範本，新建立的文件，與新建立的框架視窗之間的協同努力。 下表摘要說明哪些物件建立項目。

### <a name="object-creators"></a>物件的建立者

|建立者|建立|
|-------------|-------------|
|Application 物件|文件範本|
|文件範本|文件|
|文件範本|框架視窗|
|框架視窗|檢視|

## <a name="see-also"></a>另請參閱

[文件範本和文件/檢視建立程序](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[文件樣板建立](../mfc/document-template-creation.md)<br/>
[MFC 物件關聯性](../mfc/relationships-among-mfc-objects.md)<br/>
[建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)
