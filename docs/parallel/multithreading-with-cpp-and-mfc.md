---
title: "多執行緒 c + + 和 MFC |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 14d076865cd83837e2de218ad0189c037c78cd83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-with-c-and-mfc"></a>使用 C++ 和 MFC 進行多執行緒處理
Microsoft Foundation Class (MFC) 程式庫提供支援多執行緒應用程式。 本主題描述處理程序和執行緒，以及 MFC 方法多執行緒。  
  
 處理序是應用程式的執行個體。 例如，當您按兩下 [記事本] 圖示，開始執行 「 記事本 」 的處理序。  
  
 執行緒是執行的處理序內的路徑。 當您啟動 [記事本] 時，作業系統就會建立處理程序，並開始執行該程序的主執行緒。 當這個執行緒終止時，也會跟著處理程序。 這個主要執行緒是由啟動程式碼，函式位址的形式提供給作業系統。 通常，它是位址**主要**或`WinMain`提供的函式。  
  
 如果您想要您可以在應用程式中建立額外的執行緒。 您可能想要這樣做時不想讓使用者等候它們完成處理背景或維護工作。 MFC 應用程式中的所有執行緒都都由[CWinThread](../mfc/reference/cwinthread-class.md)物件。 在大部分情況下，您甚至不必明確建立這些物件。請改呼叫 framework helper 函式[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，它會建立`CWinThread`為您的物件。  
  
 MFC 可區別兩種執行緒： 使用者介面執行緒和背景工作執行緒。 使用者介面執行緒通常用來處理使用者輸入，並回應事件和使用者所產生的訊息。 背景工作執行緒通常用來完成工作，重新計算，例如，不需要使用者輸入。 Win32 應用程式開發介面不會區分的執行緒; 類型您只需要知道在執行緒的起始位址，讓它可以開始執行執行緒。 MFC 處理使用者介面執行緒，特別是藉由提供使用者介面中的事件訊息幫浦。 `CWinApp`是使用者介面執行緒物件的範例，因為其衍生自`CWinThread`以及處理事件和使用者所產生的訊息。  
  
 其中一個以上的執行緒可能會需要存取相同物件的情況下應該授予特別注意。 [多執行緒： 程式設計提示](../parallel/multithreading-programming-tips.md)說明技巧，您可以使用來避開在這些情況下可能發生的問題。 [多執行緒： 如何使用同步類別](../parallel/multithreading-how-to-use-the-synchronization-classes.md)描述如何使用類別，可用來同步處理多個執行緒的單一物件的存取。  
  
 撰寫和偵錯多執行緒的程式設計是原本就是很複雜，很難解釋的進行，因為您必須確定一次並非由多個執行緒存取的物件。 多執行緒主題不會教導多執行緒程式設計，如何只在多執行緒程式中使用 MFC 基本的概念。 Visual c + + 中的多執行緒的 MFC 範例說明幾個多執行緒的新增功能和 Win32 Api 的 MFC; 不包含不過，它們是僅供的起點。  
  
 如需作業系統處理程序和執行緒的方式的詳細資訊，請參閱[處理序和執行緒](http://msdn.microsoft.com/library/windows/desktop/ms684841)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
 如需 MFC 多執行緒支援的詳細資訊，請參閱下列主題：  
  
-   [多執行緒：建立使用者介面執行緒](../parallel/multithreading-creating-user-interface-threads.md)  
  
-   [多執行緒：建立背景工作執行緒](../parallel/multithreading-creating-worker-threads.md)  
  
-   [多執行緒：如何使用同步類別](../parallel/multithreading-how-to-use-the-synchronization-classes.md)  
  
-   [多執行緒：終止執行緒](../parallel/multithreading-terminating-threads.md)  
  
-   [多執行緒：程式設計提示](../parallel/multithreading-programming-tips.md)  
  
-   [多執行緒：何時使用同步類別](../parallel/multithreading-when-to-use-the-synchronization-classes.md)  
  
## <a name="see-also"></a>請參閱  
 [舊版程式碼的多執行緒支援 (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)