---
title: 建立新文件、 視窗和檢視 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MDI [MFC], creating windows
- window objects [MFC], creating
- objects [MFC], creating document objects
- MFC default objects
- frame windows [MFC], creating
- windows [MFC], MDI
- MFC, documents
- view objects [MFC], creating
- windows [MFC], creating
- overriding, default view behavior
- views [MFC], initializing
- customizing MFC default objects
- MFC, frame windows
- MFC, views
- MDI [MFC], frame windows
- child windows [MFC], creating MDI
- view objects [MFC]
- document objects [MFC], creating
- MFC default objects [MFC], customizing
- views [MFC], overriding default behavior
- initializing views [MFC]
ms.assetid: 88aa1f5f-2078-4603-b16b-a2b4c7b4a2a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89d929f4d7419e027a1018c4b0b33a4e42416613
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343411"
---
# <a name="creating-new-documents-windows-and-views"></a>建立新文件、視窗和檢視
下圖提供文件、檢視和框架視窗的建立程序概觀。 將焦點放在提供詳細資料之參與物件的其他文件。  
  
 在完成此程序之後，會存在相互合作的物件，且會儲存彼此指標。 下圖顯示物件建立的序列。 您可以遵循圖表到圖表的序列。  
  
 ![建立文件順序](../mfc/media/vc387l1.gif "vc387l1")  
建立文件的序列  
  
 ![框架視窗建立順序](../mfc/media/vc387l2.png "vc387l2")  
建立框架視窗的序列  
  
 ![建立檢視順序](../mfc/media/vc387l3.gif "vc387l3")  
建立檢視的序列  
  
 如需架構如何初始化新的文件、 檢視和框架視窗物件的資訊，請參閱 < 類別[CDocument](../mfc/reference/cdocument-class.md)， [CView](../mfc/reference/cview-class.md)， [CFrameWnd](../mfc/reference/cframewnd-class.md)， [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)，和[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) MFC 程式庫參考中。 另請參閱[技術提示 22](../mfc/tn022-standard-commands-implementation.md)，其中說明建立和初始化程序進一步的 framework 的標準命令可用於其討論`New`和**開啟**中的項目**檔案**功能表。  
  
##  <a name="_core_initializing_your_own_additions_to_these_classes"></a> 初始化您自己加入至這些類別  
 上述圖也建議可以覆寫成員函式以初始化應用程式物件的點。 在您檢視類別的 `OnInitialUpdate` 覆寫，是初始化檢視的最佳位置。 在建立框架視窗，以及並在框架視窗內的檢視附加至其文件後，會立即呼叫 `OnInitialUpdate`。 例如，若您的視圖是捲動檢視 (衍生自 `CScrollView` 而非 `CView`)，您應該根據您的 `OnInitialUpdate` 覆寫的文件大小來設定視圖大小。 (此程序所述類別的描述[CScrollView](../mfc/reference/cscrollview-class.md)。)您可以覆寫**CDocument**成員函式`OnNewDocument`和`OnOpenDocument`提供特定應用程式初始化文件。 通常必須覆寫兩個，因為文件可以用兩種方式建立。  
  
 在大部分情況下，您的覆寫應該呼叫基底類別版本。 如需詳細資訊，請參閱類別的具名的成員函式[CDocument](../mfc/reference/cdocument-class.md)， [CView](../mfc/reference/cview-class.md)， [CFrameWnd](../mfc/reference/cframewnd-class.md)，和[CWinApp](../mfc/reference/cwinapp-class.md) MFC 中程式庫參考。  
  
## <a name="see-also"></a>另請參閱  
 [文件範本和文件/檢視建立程序](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [建立文件範本](../mfc/document-template-creation.md)   
 [文件/檢視建立](../mfc/document-view-creation.md)   
 [MFC 物件關聯性](../mfc/relationships-among-mfc-objects.md)

