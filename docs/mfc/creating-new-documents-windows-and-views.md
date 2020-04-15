---
title: 建立新文件、視窗和檢視
ms.date: 11/19/2018
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
ms.openlocfilehash: aa1c58b02df92d79ca9915032b97fb5c0e2eaffc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371671"
---
# <a name="creating-new-documents-windows-and-views"></a>建立新文件、視窗和檢視

下圖提供文件、檢視和框架視窗的建立程序概觀。 將焦點放在提供詳細資料之參與物件的其他文件。

在完成此程序之後，會存在相互合作的物件，且會儲存彼此指標。 下圖顯示物件建立的序列。 您可以遵循圖表到圖表的序列。

![建立文件順序](../mfc/media/vc387l1.gif "建立文件順序") <br/>
建立文件的序列

![框架視窗建立順序](../mfc/media/vc387l2.png "框架視窗建立順序") <br/>
建立框架視窗的序列

![建立檢視順序](../mfc/media/vc387l3.gif "建立檢視順序") <br/>
建立檢視的序列

有關框架如何初始化新文檔、檢視和框架視窗物件的資訊,請參閱 MFC 庫參考中的類 CDocument、CView、CFramewnd、CMDIFramewnd 和[CMDIChildwnd。](../mfc/reference/cmdichildwnd-class.md) [CDocument](../mfc/reference/cdocument-class.md) [CView](../mfc/reference/cview-class.md) [CFrameWnd](../mfc/reference/cframewnd-class.md) [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) 另請參閱[技術說明 22](../mfc/tn022-standard-commands-implementation.md),其中在討論框架在 **「檔案**」選單上的 **「新建**」和 **「打開」** 項的標準命令時,進一步解釋了創建和初始化過程。

## <a name="initializing-your-own-additions-to-these-classes"></a><a name="_core_initializing_your_own_additions_to_these_classes"></a>初始化自己對這些類別的新增

上述圖也建議可以覆寫成員函式以初始化應用程式物件的點。 在您檢視類別的 `OnInitialUpdate` 覆寫，是初始化檢視的最佳位置。 在建立框架視窗，以及並在框架視窗內的檢視附加至其文件後，會立即呼叫 `OnInitialUpdate`。 例如，若您的視圖是捲動檢視 (衍生自 `CScrollView` 而非 `CView`)，您應該根據您的 `OnInitialUpdate` 覆寫的文件大小來設定視圖大小。 (此過程在類[CScrollView](../mfc/reference/cscrollview-class.md)的說明中描述。您可以重寫`CDocument`成員函`OnNewDocument`數`OnOpenDocument`並提供 特定於應用程式的文檔初始化。 通常必須覆寫兩個，因為文件可以用兩種方式建立。

在大部分情況下，您的覆寫應該呼叫基底類別版本。 有關詳細資訊,請參閱 MFC 庫參考中的類 CDocument、CView、CFramewnd 和[CWinApp](../mfc/reference/cwinapp-class.md)[CDocument](../mfc/reference/cdocument-class.md)[CView](../mfc/reference/cview-class.md)[CFrameWnd](../mfc/reference/cframewnd-class.md)的命名成員函數。

## <a name="see-also"></a>另請參閱

[文件樣本與文件/檢視建立程序](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[文件樣板建立](../mfc/document-template-creation.md)<br/>
[文件/檢視建立](../mfc/document-view-creation.md)<br/>
[MFC 物件關聯性](../mfc/relationships-among-mfc-objects.md)
