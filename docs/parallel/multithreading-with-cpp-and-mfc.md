---
title: 使用 C++ 和 MFC 進行多執行緒處理
ms.date: 08/27/2018
helpviewer_keywords:
- MFC [C++], multithreading
- threading [C++], MFC
- worker threads [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], about threading
- CWinThread class, purpose of
- multithreading [C++], MFC
- threading [MFC]
- user interface threads [C++]
ms.assetid: 979605f8-3988-44b5-ac9c-b8cce7fcce14
ms.openlocfilehash: eaf28404b06e9b0bf6126d8bbc140bf46cff37da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512008"
---
# <a name="multithreading-with-c-and-mfc"></a>使用 C++ 和 MFC 進行多執行緒處理

Microsoft Foundation Class (MFC) 程式庫提供多執行緒應用程式的支援。 本主題描述處理常式和執行緒, 以及 MFC 方法來進行多執行緒處理。

進程是應用程式的執行中實例。 例如, 當您按兩下 [記事本] 圖示時, 就會啟動執行 [記事本] 的進程。

執行緒是在進程內執行的路徑。 當您啟動 [記事本] 時, 作業系統會建立進程, 並開始執行該進程的主要執行緒。 當這個執行緒終止時, 就會執行此程式。 啟動程式碼會以函式位址的形式, 將此主要執行緒提供給作業系統。 通常, 這是所提供之`main`或`WinMain`函式的位址。

如有需要, 您可以在應用程式中建立額外的執行緒。 當您不想讓使用者等待他們完成時, 您可能會想要這樣做來處理背景或維護工作。 MFC 應用程式中的所有線程都是由[CWinThread](../mfc/reference/cwinthread-class.md)物件表示。 在大部分的情況下, 您甚至不需要明確地建立這些物件。相反地, 呼叫架構協助程式函式[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), `CWinThread`這會為您建立物件。

MFC 會區分兩種類型的執行緒: 使用者介面執行緒和背景工作執行緒。 使用者介面執行緒通常用來處理使用者輸入, 並回應使用者所產生的事件和訊息。 背景工作執行緒通常用來完成不需要使用者輸入的作業, 例如重新計算。 WIN32 API 不會區分執行緒的類型;它只需要知道執行緒的起始位址, 就可以開始執行執行緒。 MFC 會在使用者介面中提供事件的訊息抽取, 以特別處理使用者介面執行緒。 `CWinApp`是使用者介面執行緒物件的範例, 因為它衍生自`CWinThread` , 並處理使用者所產生的事件和訊息。

有一個以上的執行緒可能需要存取相同的物件時, 應該特別注意。 [多執行緒：程式設計](multithreading-programming-tips.md)秘訣說明您可以用來解決這些情況下可能發生之問題的技術。 [多執行緒：如何使用同步處理類別](multithreading-how-to-use-the-synchronization-classes.md)說明如何使用可用來將多個執行緒的存取同步至單一物件的類別。

撰寫和偵測多執行緒程式設計本身是一項複雜且棘手的工作, 因為您必須確保一次不會有一個以上的執行緒存取物件。 多執行緒主題不會教多執行緒程式設計的基本概念, 只是如何在多執行緒程式中使用 MFC。 包含在視覺效果C++中的多執行緒 MFC 範例會說明幾個多執行緒新增功能, 以及 MFC 不包含的 Win32 api;不過, 它們的目的只是一個起點。

如需作業系統如何處理進程和執行緒的詳細資訊, 請參閱 Windows SDK 中的[進程和執行緒](/windows/win32/ProcThread/processes-and-threads)。

如需 MFC 多執行緒支援的詳細資訊, 請參閱下列主題:

- [多執行緒：建立使用者介面執行緒](multithreading-creating-user-interface-threads.md)

- [多執行緒：建立背景工作執行緒](multithreading-creating-worker-threads.md)

- [多執行緒：如何使用同步類別](multithreading-how-to-use-the-synchronization-classes.md)

- [多執行緒：終止執行緒](multithreading-terminating-threads.md)

- [多執行緒：程式設計提示](multithreading-programming-tips.md)

- [多執行緒：何時使用同步類別](multithreading-when-to-use-the-synchronization-classes.md)

## <a name="see-also"></a>另請參閱

[舊版程式碼的多執行緒支援 (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)
