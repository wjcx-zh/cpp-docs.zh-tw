---
title: "多執行緒：建立背景工作執行緒 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "背景工作 [C++]"
  - "多執行緒 [C++], 背景工作執行緒"
  - "執行緒 [C++], 建立執行緒"
  - "執行緒 [C++], 不需使用者輸入"
  - "執行緒 [C++], 背景工作執行緒"
  - "執行緒 [MFC], 背景工作執行緒"
  - "背景工作執行緒 [C++]"
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多執行緒：建立背景工作執行緒
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

背景工作執行緒通常用來處理背景工作，使用者應該不需要等待背景工作以繼續使用您的程式。  例如重新計算和背景列印之類的工作都是背景工作執行緒的很好範例。  本主題詳細說明建立背景工作執行緒的必要步驟。  主題包括：  
  
-   [啟動執行緒](#_core_starting_the_thread)  
  
-   [實作控制函式](#_core_implementing_the_controlling_function)  
  
-   [範例](#_core_controlling_function_example)  
  
 建立背景工作執行緒是相對較簡單的工作。  只需要兩個步驟便可執行您的執行緒：實作控制函式和啟動執行緒。  並不需要從 [CWinThread](../../mfc/reference/cwinthread-class.md) 來衍生類別。  如果您需要 `CWinThread` 的特殊版本，您可以衍生類別，但大多數簡單的背景工作執行緒都不需要這麼做。  您可以使用 `CWinThread`，無須修改。  
  
##  <a name="_core_starting_the_thread"></a> 啟動執行緒  
 `AfxBeginThread` 有兩個多載版本：只能建立背景工作執行緒的版本，以及可以建立使用者介面執行緒和背景工作執行緒的版本。  若要使用第一個多載，開始執行您的背景工作執行緒，請呼叫 [AfxBeginThread](../Topic/AfxBeginThread.md)，提供下列資訊：  
  
-   控制函式的位址。  
  
-   要傳遞至控制函式的參數。  
  
-   \(選擇項\) 想要的執行緒優先權。  預設值是一般優先權。  如需可用的優先權層級，請參閱 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的 [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)。  
  
-   \(選擇項\) 想要的執行緒堆疊大小。  預設為與建立的執行緒堆疊大小相同。  
  
-   \(選擇項\) **CREATE\_SUSPENDED** 如果您要將執行緒建立在暫停狀態。  預設值為 0，或是正常啟動執行緒。  
  
-   \(選擇項\) 想要的安全屬性。  預設為與父執行緒相同的存取。  如需這個安全資訊格式的詳細資訊，請參閱 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的 [SECURITY\_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)。  
  
 `AfxBeginThread` 會為您建立並且初始化 `CWinThread` 物件，將它啟動並傳回它的位址，讓您稍後可以加以參考。  整個程序都會進行檢查，確保建立的任何部分萬一失敗時，所有物件都會適當地解除配置。  
  
##  <a name="_core_implementing_the_controlling_function"></a> 實作控制函式  
 控制函式會定義執行緒。  當這個函式被輸入時，執行緒會啟動，並且當它結束時，執行緒會結束。  這個函式應該具有下列的原型：  
  
```  
UINT MyControllingFunction( LPVOID pParam );  
```  
  
 這個參數是單一值。  函式在這個參數中接收的值就是執行緒物件建立時傳遞至建構函式的值。  控制函式可用它選擇的方式來轉譯這個值。  可以把它當成純量值或指向包含多個參數的結構之指標，或者可以忽略它。  如果參數參考結構，則結構不僅可以用來從呼叫端傳遞資料到執行緒，也可以從執行緒傳遞資料回呼叫端。  如果您使用這種結構將資料傳回呼叫端，當結果準備好時執行緒會需要告知呼叫端。  如需從背景工作執行緒到呼叫端的通訊的詳細資訊，請參閱[多執行緒：程式設計提示](../../parallel/multithreading-programming-tips.md)。  
  
 當函式結束時，它應該傳回 **UINT** 值，指示終止的原因。  通常，結束碼 0 代表成功，其他值則代表不同類型的錯誤。  這完全與實作相關。  有些執行緒會維持物件的使用計數，並且傳回該物件的目前使用次數。  若要了解應用程式如何擷取這個值，請參閱[多執行緒：結束執行緒](../../parallel/multithreading-terminating-threads.md)。  
  
 在以 MFC 程式庫撰寫的多執行緒程式中可進行的動作，會有某些限制。  如需這些限制的說明以及使用執行緒的其他提示，請參閱[多執行緒：程式設計提示](../../parallel/multithreading-programming-tips.md)。  
  
##  <a name="_core_controlling_function_example"></a> 控制函式範例  
 在下列程式碼中，示範了如何定義控制函式並從程式的另一部分來使用它。  
  
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
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [多執行緒：建立使用者介面執行緒](../../parallel/multithreading-creating-user-interface-threads.md)  
  
## 請參閱  
 [使用 C\+\+ 和 MFC 進行多執行緒處理](../../parallel/multithreading-with-cpp-and-mfc.md)