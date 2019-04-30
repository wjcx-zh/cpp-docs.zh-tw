---
title: 架構如何呼叫您的程式碼
ms.date: 11/04/2016
helpviewer_keywords:
- control flow [MFC], MFC framework and your code
- events [MFC], command routing in MFC
- command routing [MFC], framework
- command handling [MFC], calling handlers and code in MFC
- events [MFC], event-driven programming
- MFC, calling code from
- MFC, calling code
- application-specific events [MFC]
- command routing [MFC], MFC
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
ms.openlocfilehash: 81b0749167391a841badff5494023a2ca5d3147e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407948"
---
# <a name="how-the-framework-calls-your-code"></a>架構如何呼叫您的程式碼

了解您的原始程式碼和 MFC 架構中程式碼之間的關聯性很重要。 當應用程式執行時，大部分的控制流程會位於架構的程式碼中。 當使用者選擇命令並編輯檢視中的資料時，架構會管理從 Windows 取得訊息的訊息迴圈。 架構可以自行處理的事件甚至不需要仰賴您的程式碼。 例如，架構知道如何回應使用者命令來關閉視窗並結束應用程式。 當它處理這些工作時，架構會使用訊息處理常式和 C++ 虛擬函式讓您有機會回應這些事件。 您的程式碼無法控制；但架構則可以。

架構會呼叫您的應用程式特定事件的程式碼。 例如，當使用者選擇某個功能表命令時，架構會沿著 C++ 物件序列的順序進行路由：目前檢視和框架視窗、與檢視相關聯的文件、文件的文件範本和應用程式物件。 如果其中一個物件可以處理命令，則它會呼叫適當的訊息處理函式。 對於任何指定的命令，所呼叫的程式碼可能是您的、也可能是架構的。

這個安排對於具有傳統 Windows 或事件驅動程式設計經驗的人來說，應該是有些熟悉的。

在相關主題中，您將閱讀架構在初始化和執行應用程式時會做什麼，接著會在應用程式結束時進行清除。 您也會了解要在需要調整的程式碼位置。

如需詳細資訊，請參閱[類別 CWinApp:應用程式類別](../mfc/cwinapp-the-application-class.md)並[文件範本和文件/檢視建立程序](../mfc/document-templates-and-the-document-view-creation-process.md)。

## <a name="see-also"></a>另請參閱

[在架構上建置](../mfc/building-on-the-framework.md)
