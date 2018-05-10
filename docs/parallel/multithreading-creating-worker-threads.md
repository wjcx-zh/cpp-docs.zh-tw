---
title: 多執行緒： 建立背景工作執行緒 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], worker threads
- background tasks [C++]
- threading [C++], worker threads
- worker threads [C++]
- threading [C++], creating threads
- threading [MFC], worker threads
- threading [C++], user input not required
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 175fc018ddba436f9a331f861a492dcd43e1ec1e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="multithreading-creating-worker-threads"></a>多執行緒：建立背景工作執行緒
背景工作執行緒通常用來處理使用者應該不需要等待要繼續使用您的應用程式的背景工作。 重新計算和幕後列印等工作是背景工作執行緒的良好範例。 本主題詳細說明建立工作者執行緒的必要步驟。 主題包括：  
  
-   [啟動執行緒](#_core_starting_the_thread)  
  
-   [實作控制函式](#_core_implementing_the_controlling_function)  
  
-   [範例](#_core_controlling_function_example)  
  
 建立背景工作執行緒是相當簡單的工作。 只有兩個步驟，才能執行您的執行緒： 實作控制函式，以及啟動執行緒。 不需要自[CWinThread](../mfc/reference/cwinthread-class.md)。 如果您需要特殊版本的衍生類別`CWinThread`，但它不是必要的最簡單的背景工作執行緒。 您可以使用`CWinThread`而不需修改。  
  
##  <a name="_core_starting_the_thread"></a> 啟動執行緒  
 有兩個多載的版本`AfxBeginThread`： 只能建立背景工作執行緒的其中一個，另一個則可以建立使用者介面執行緒和背景工作執行緒。 若要開始使用第一個多載在背景工作執行緒執行，請呼叫[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，提供下列資訊：  
  
-   控制函式的位址。  
  
-   要傳遞給控制函式的參數。  
  
-   （選擇性）所需的執行緒的優先權。 預設為一般優先順序。 如需可用的優先順序層級的詳細資訊，請參閱[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
-   （選擇性）執行緒的所需的堆疊大小。 預設為相同大小堆疊與建立的執行緒。  
  
-   （選擇性）**CREATE_SUSPENDED**如果您想要在暫停狀態中建立的執行緒。 預設值為 0，或以正常方式啟動執行緒。  
  
-   （選擇性）所需的安全性屬性。 預設為在父執行緒與相同的存取。 此安全性資訊的格式的相關資訊，請參閱[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
 `AfxBeginThread` 建立並初始化`CWinThread`，物件開始，並傳回其位址，以便日後參考。 整個程序進行檢查以確定所有物件都都會解除配置建立的任何部分失敗。  
  
##  <a name="_core_implementing_the_controlling_function"></a> 實作控制函式  
 控制函式定義的執行緒。 此函式輸入時，執行緒正常啟動，且當其存在時，執行緒終止。 此函式應該具有下列原型：  
  
```  
UINT MyControllingFunction( LPVOID pParam );  
```  
  
 參數是單一值。 建立執行緒物件時傳遞給建構函式的值為函式會接收此參數中的值。 控制函式可將此值則會選擇的任何方式解譯。 可以將它視為純量值或指標，此結構包含多個參數，或忽略它。 如果參數參考的結構，結構可以用來將資料從呼叫端傳遞至執行緒，不僅也將從執行緒傳回的資料傳遞至呼叫端。 如果您將資料傳遞至呼叫端使用這種結構，就必須結果就緒時通知呼叫端執行緒。 關於通訊背景工作執行緒從呼叫端的資訊，請參閱[多執行緒： 程式設計提示](../parallel/multithreading-programming-tips.md)。  
  
 當函式結束時，它應該傳回**UINT**值，指出終止的原因。 一般而言，這個結束代碼是 0 代表成功，其他值則代表不同類型的錯誤。 這是單純地實作而定。 有些執行緒可能會維護物件的使用計數，並傳回該物件會使用目前的數目。 若要查看應用程式可以擷取此值的方式，請參閱[多執行緒： 結束執行緒](../parallel/multithreading-terminating-threads.md)。  
  
 有一些限制您可以在使用 MFC 程式庫撰寫多執行緒程式中執行。 如需說明這些限制和其他使用執行緒的秘訣，請參閱[多執行緒： 程式設計提示](../parallel/multithreading-programming-tips.md)。  
  
##  <a name="_core_controlling_function_example"></a> 控制函式範例  
 下列範例會示範如何定義控制函式，並從另一個部分的程式使用它。  
  
```  
UINT MyThreadProc( LPVOID pParam )  
{  
    CMyObject* pObject = (CMyObject*)pParam;  
  
    if (pObject == NULL ||  
        !pObject->IsKindOf(RUNTIME_CLASS(CMyObject)))  
    return 1;   // if pObject is not valid  
  
    // do something with 'pObject'  
  
    return 0;   // thread completed successfully  
}  
  
// inside a different function in the program  
.  
.  
.  
pNewObject = new CMyObject;  
AfxBeginThread(MyThreadProc, pNewObject);  
.  
.  
.  
```  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [多執行緒：建立使用者介面執行緒](../parallel/multithreading-creating-user-interface-threads.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用 C++ 和 MFC 進行多執行緒處理](../parallel/multithreading-with-cpp-and-mfc.md)