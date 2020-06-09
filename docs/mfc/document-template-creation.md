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
ms.openlocfilehash: 952a383792eb3a4d0a4ed1b3e24dd82f7fa644cf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615791"
---
# <a name="document-template-creation"></a>文件樣板建立

當您在 [檔案] 功能表中建立新的檔以回應**新**的或**開啟**的命令時，檔範本也會建立新的框架視窗，以供您用來查看**檔**。

檔範本的函式會指定範本能夠建立哪些類型的檔、視窗和 views。 這是由您傳遞至檔範本函式的引數所決定。 下列程式碼說明如何建立範例應用程式的[CMultiDocTemplate](reference/cmultidoctemplate-class.md) ：

[!code-cpp[NVC_MFCDocView#7](codesnippet/cpp/document-template-creation_1.cpp)]

新物件的指標 `CMultiDocTemplate` 會當做[AddDocTemplate](reference/cwinapp-class.md#adddoctemplate)的引數使用。 此函式的引數 `CMultiDocTemplate` 包含與檔案類型的功能表和加速器相關聯的資源識別碼，以及三種[RUNTIME_CLASS](reference/run-time-object-model-services.md#runtime_class)宏的用法。 `RUNTIME_CLASS`傳回名為之 c + + 類別的[CRuntimeClass](reference/cruntimeclass-structure.md)物件，其為其引數。 `CRuntimeClass`傳遞至檔範本處理常式的三個物件，會提供在檔建立程式期間建立指定類別之新物件所需的資訊。 這個範例會示範如何建立檔範本，以建立 `CScribDoc` `CScribView` 附加物件的物件。 這些視圖是以標準 MDI 子框架視窗來框住。

## <a name="see-also"></a>另請參閱

[檔範本和檔/視圖建立程式](document-templates-and-the-document-view-creation-process.md)<br/>
[文件/檢視建立](document-view-creation.md)<br/>
[MFC 物件關聯性](relationships-among-mfc-objects.md)<br/>
[建立新文件、視窗和檢視](creating-new-documents-windows-and-views.md)
