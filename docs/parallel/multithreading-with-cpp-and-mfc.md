---
title: 使用 c + + 和 MFC 進行多執行緒處理 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1f5f1ea1d8d6578b631da772522a0a852d11c89
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "43132190"
---
# <a name="multithreading-with-c-and-mfc"></a>使用 C++ 和 MFC 進行多執行緒處理
Microsoft Foundation Class (MFC) 程式庫會提供支援多執行緒應用程式。 本主題描述處理程序和執行緒，以及的 MFC 方法多執行緒。  
  
處理序是應用程式的執行個體。 比方說，當您按兩下 [記事本] 圖示，您會啟動執行記事本的處理序。  
  
執行緒是執行的處理序中的路徑。 當您啟動 [記事本] 時，作業系統會建立一個處理序，並開始執行該程序主要執行緒。 當這個執行緒終止時，處理序。 這個主要執行緒是由啟動程式碼，函式位址的形式提供給作業系統。 通常，它是位址`main`或`WinMain`提供的函式。  
  
如果您想要您可以在您的應用程式中建立額外的執行緒。 您可能想要這樣做時不想讓使用者等候排程完成處理背景或維護工作。 MFC 應用程式中的所有執行緒都都由[CWinThread](../mfc/reference/cwinthread-class.md)物件。 在大部分情況下，您甚至不必明確建立這些物件;改為呼叫架構 helper 函式[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，這會建立`CWinThread`為您的物件。  
  
MFC 會分辨兩種類型的執行緒： 使用者介面執行緒和背景工作執行緒。 使用者介面執行緒通常用來處理使用者輸入，並回應事件和使用者所產生的訊息。 背景工作執行緒通常用來完成工作，例如重新計算，不需要使用者輸入。 Win32 API 不會區分的執行緒; 的類型它只需要知道執行緒的開始位址，就可以開始執行執行緒。 MFC 處理使用者介面執行緒，特別是藉由提供使用者介面中的事件訊息幫浦。 `CWinApp` 是使用者介面執行緒物件的範例，因為它衍生自`CWinThread`和處理事件和使用者所產生的訊息。  
  
其中多個執行緒可能會需要存取相同物件的情況下，應該會提供特別注意。 [多執行緒： 程式設計提示](multithreading-programming-tips.md)說明技巧，您可以使用來解決在這些情況下可能發生的問題。 [多執行緒： 如何使用同步類別](multithreading-how-to-use-the-synchronization-classes.md)描述如何使用可用來同步處理從多個執行緒存取單一物件的類別。  
  
撰寫和偵錯多執行緒的程式設計是原本就複雜並難以處理的工作，因為您必須確定一次不由多個執行緒存取的物件。 多執行緒主題不會教導多執行緒程式設計，如何在多執行緒程式中使用 MFC 基本的概念。 包含 Visual c + + 中的多執行緒的 MFC 範例說明幾個多執行緒的新增功能和 Win32 Api 的 MFC; 不包含不過，它們只主要做為起點。  
  
如需作業系統處理程序和執行緒的方式的詳細資訊，請參閱[處理序和執行緒](/windows/desktop/ProcThread/processes-and-threads)Windows SDK 中。  
  
如需 MFC 多執行緒支援的詳細資訊，請參閱下列主題：  
  
- [多執行緒：建立使用者介面執行緒](multithreading-creating-user-interface-threads.md)  
  
- [多執行緒：建立背景工作執行緒](multithreading-creating-worker-threads.md)  
  
- [多執行緒：如何使用同步類別](multithreading-how-to-use-the-synchronization-classes.md)  
  
- [多執行緒：終止執行緒](multithreading-terminating-threads.md)  
  
- [多執行緒：程式設計提示](multithreading-programming-tips.md)  
  
- [多執行緒：何時使用同步類別](multithreading-when-to-use-the-synchronization-classes.md)  
  
## <a name="see-also"></a>另請參閱  
 
[舊版程式碼的多執行緒支援 (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)