---
title: OLE 背景：Implementation Strategies
ms.date: 11/04/2016
helpviewer_keywords:
- OLE [MFC], development strategy
- OLE applications [MFC], implementing OLE
- applications [OLE], implementing OLE
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
ms.openlocfilehash: 40c74d48b76921f770740602a39d28804a7e3c09
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284810"
---
# <a name="ole-background-implementation-strategies"></a>OLE 背景：Implementation Strategies

視您的應用程式而定，實作新增 OLE 支援的可行策略有四種：

- 撰寫新的應用程式。

   這種情況通常需要的工作最少。 執行 MFC 應用程式精靈並選取 [進階功能] 或 [複合文件支援] 以建立基本架構應用程式。 如需這些選項，以及他們如何資訊，請參閱文章[建立 MFC EXE 程式](../mfc/reference/mfc-application-wizard.md)。

- 您有程式是以不支援 OLE 的 MFC 程式庫 2.0 版或更新版本撰寫。

   如上述，以 MFC 應用程式精靈建立新的應用程式，然後複製新應用程式的程式碼並貼至現有的應用程式。 這適用於伺服器、容器或自動化應用程式。 請參閱 MFC [SCRIBBLE](../visual-cpp-samples.md)範例如需此策略的範例。

- 您擁有實作 OLE 1.0 版支援的 MFC 程式庫程式。

   請參閱[MFC 技術提示 41](../mfc/tn041-mfc-ole1-migration-to-mfc-ole-2.md)此轉換策略。

- 您有不是使用 Microsoft Foundation Classes 撰寫的應用程式，而且可能具有或者沒有實作的 OLE 支援。

   這種情況需要的工作最多。 一種方法是以第一項策略的方式建立新應用程式，然後複製您現有的程式碼並貼到其中。 如果現有的程式碼是以 C 撰寫，則您可能需要修改程式碼才能以 C++ 程式碼編譯。 如果您的 C 程式碼呼叫 Windows API，則您不需要變更程式碼就可使用 MFC。 這個方法可能會需要變更您的程式結構以支援 Microsoft Foundation Classes 2.0 以上版本使用的文件/檢視架構。 如需有關此架構的詳細資訊，請參閱[技術提示 25](../mfc/tn025-document-view-and-frame-creation.md)。

一旦您決定策略，您應該參閱[容器](../mfc/containers.md)或是[伺服器](../mfc/servers.md)文章 （取決於您要撰寫的應用程式類型），或檢查範例程式，或兩者。 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)並[HIERSVR](../visual-cpp-samples.md)示範如何分別實作容器和伺服器的各個層面。 在這些文件中的幾個部分中，將會請您參考這些範例中的某些函式，作為所討論的技術的範例。

## <a name="see-also"></a>另請參閱

[OLE 背景](../mfc/ole-background.md)<br/>
[容器：實作容器](../mfc/containers-implementing-a-container.md)<br/>
[伺服器：實作伺服器](../mfc/servers-implementing-a-server.md)<br/>
[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)
