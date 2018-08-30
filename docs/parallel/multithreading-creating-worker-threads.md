---
title: 多執行緒： 建立背景工作執行緒在 MFC |Microsoft Docs
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
ms.openlocfilehash: 1057d8992f6554d4d5fbbfd93b383e2ddd9dab53
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211633"
---
# <a name="multithreading-creating-worker-threads-in-mfc"></a>多執行緒： 建立背景工作執行緒在 MFC 中
背景工作執行緒通常會用來處理背景工作，使用者應該不需要等候以繼續使用您的應用程式中。 重新計算和背景列印等工作是背景工作執行緒的良好範例。 本主題詳細說明建立背景工作執行緒所需的步驟。 主題包括：  
  
- [啟動執行緒](#_core_starting_the_thread)  
  
- [實作控制函式](#_core_implementing_the_controlling_function)  
  
- [範例](#_core_controlling_function_example)  
  
建立背景工作執行緒是相當簡單的工作。 只有兩個步驟，才能取得您執行的執行緒： 實作控制函式和啟動執行緒。 您不需要衍生的類別[CWinThread](../mfc/reference/cwinthread-class.md)。 如果您需要的特殊版本，您可以衍生一個類別`CWinThread`，但它不是必要的最簡單的背景工作執行緒。 您可以使用`CWinThread`而不需修改。  
  
##  <a name="_core_starting_the_thread"></a> 啟動執行緒  
 
有兩個多載的版本`AfxBeginThread`： 一個只能建立背景工作執行緒，就可以建立使用者介面執行緒和背景工作執行緒的另一個。 若要開始執行您使用第一個多載的背景工作執行緒，請呼叫[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，提供下列資訊：  
  
- 控制函式的位址。  
  
- 要傳遞至控制函式的參數。  
  
- （選擇性）想要的執行緒優先權。 預設值是一般優先權。 如需可用的優先權層級的詳細資訊，請參閱[SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) Windows SDK 中。  
  
- （選擇性）執行緒所需的堆疊大小。 預設值是相同的大小堆疊，與建立的執行緒。  
  
- （選擇性）如果您想要在暫停狀態中建立的執行緒，CREATE_SUSPENDED。 預設值為 0，或以正常方式啟動執行緒。  
  
- （選擇性）所需的安全性屬性。 預設為與父執行緒相同的存取權。 此安全性資訊的格式的相關資訊，請參閱[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) Windows SDK 中。  
  
`AfxBeginThread` 建立並初始化`CWinThread`物件，它啟動，並傳回它的位址，因此您可以稍後參考它。 整個程序進行檢查以確定所有物件都是已解除配置正確建立的任何部分萬一失敗。  
  
##  <a name="_core_implementing_the_controlling_function"></a> 實作控制函式  
 
控制函式會定義執行緒。 輸入此函式之後，請在執行緒啟動時，並當其存在時，執行緒終止。 此函式應該具有下列原型：  
  
```  
UINT MyControllingFunction( LPVOID pParam );  
```  
  
參數是單一值。 函式會接收此參數中的值會是執行緒物件建立時傳遞至建構函式的值。 控制函式可以解譯以任何方式，它會選擇此值。 它可以視為純量值的指標或結構，包含多個參數，或可以忽略它。 如果參數參考結構，結構可用來將資料從呼叫端傳遞至執行緒，不僅要將資料從執行緒傳遞給呼叫者。 如果您使用這種結構將資料傳遞至呼叫端時，執行緒會需要告知呼叫端，當結果準備好。 如需從背景工作執行緒通訊給呼叫端資訊，請參閱[多執行緒： 程式設計提示](multithreading-programming-tips.md)。  
  
當函式結束時，它應該傳回 UINT 值，指出終止的原因。 一般而言，這個結束代碼是 0 代表成功，其他值則代表不同類型的錯誤。 這是完全與實作相關。 有些執行緒可能會維護物件的使用計數，並傳回該物件會使用目前的數目。 若要查看應用程式可以擷取此值的方式，請參閱[多執行緒： 結束執行緒](multithreading-terminating-threads.md)。  
  
有可進行撰寫與 MFC 程式庫的多執行緒程式中的一些限制。 如需描述這些限制和其他使用執行緒的秘訣，請參閱[多執行緒： 程式設計提示](multithreading-programming-tips.md)。  
  
##  <a name="_core_controlling_function_example"></a> 控制函式範例  
 
下列範例示範如何定義控制函式，並從另一個部分的程式使用它。  
  
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
  
- [多執行緒：建立使用者介面執行緒](multithreading-creating-user-interface-threads.md)  
  
## <a name="see-also"></a>另請參閱  
 
[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)