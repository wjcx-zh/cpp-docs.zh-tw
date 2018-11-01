---
title: 文件樣板建立
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
ms.openlocfilehash: f5c0691deab3d475a72cda0e86d681ea0c4ddfa0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480167"
---
# <a name="document-template-creation"></a>文件樣板建立

當建立新的文件，以回應**新增**或**開啟**命令**檔案**功能表上，文件範本也會建立新的框架視窗，以檢視文件。

文件範本建構函式會指定哪些類型的文件、 視窗和範本可以建立的檢視。 這取決於您將傳遞至文件範本建構函式的引數。 下列程式碼說明建立[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)的範例應用程式：

[!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/cpp/document-template-creation_1.cpp)]

新指標`CMultiDocTemplate`物件做為引數[Initinstance](../mfc/reference/cwinapp-class.md#adddoctemplate)。 引數`CMultiDocTemplate`建構函式包含文件類型的功能表和快速鍵，相關聯的資源識別碼和三個用途[RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)巨集。 `RUNTIME_CLASS` 會傳回[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)命名為其引數的 c + + 類別的物件。 三個`CRuntimeClass`物件傳遞至文件範本建構函式提供文件的建立程序期間建立的指定類別的新物件所需的資訊。 此範例示範建立文件範本，建立`CScribDoc`具有物件`CScribView`附加的物件。 檢視是由標準的 MDI 子框架視窗框住。

## <a name="see-also"></a>另請參閱

[文件範本和文件/檢視建立程序](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[文件/檢視建立](../mfc/document-view-creation.md)<br/>
[MFC 物件關聯性](../mfc/relationships-among-mfc-objects.md)<br/>
[建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)

